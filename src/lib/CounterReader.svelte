<script>
  import { onDestroy } from "svelte";

  export let app;
  import {
    collection,
    getFirestore,
    increment,
    onSnapshot,
    query,
    orderBy,
    limit,
    Timestamp,
  } from "firebase/firestore";
  const db = getFirestore(app);
  const q = query(collection(db, "counts"), orderBy("date", "desc"), limit(5));

  $: counts = [];
  $: error = "";
  const unsubscribe = onSnapshot(
    q,
    (querySnapshot) => {
      const allCounts = [];
      querySnapshot.forEach((doc) => {
        allCounts.push({ id: doc.id, ...doc.data() });
      });
      counts = allCounts;
    },
    (e) => (error = e.message)
  );

  onDestroy(() => {
    unsubscribe();
  });
</script>

<h2>Last 5</h2>

<section>
  {#each counts as count}
    <div class="count-container card">
      <div><span>ID: </span><span>{count.id}</span></div>
      <div>
        <span>Time: </span><span
          >{count.date.toDate().toLocaleTimeString()}</span
        >
      </div>
      <div><span>Count: </span><span>{count.count}</span></div>
    </div>
  {/each}
  {#if error}
    <div class="error">
      {error}
    </div>
  {/if}
</section>

<style>
  section {
    display: flex;
    justify-content: center;
    gap: 0.5rem;
    padding: 1rem;
  }
  .count-container {
    display: flex;
    flex-direction: column;
    align-items: start;
    max-width: 300px;

    border-radius: 8px;
    border: 1px solid transparent;
    padding: 0.6em 1.2em;
    font-size: 1em;
    font-weight: 500;
    font-family: inherit;
    background-color: #2f2f2f;
  }
  .error {
    background-color: red;
    font-size: 2rem;
    padding: 1rem;
  }
</style>
