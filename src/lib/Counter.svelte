<script>
  export let app;
  import { addDoc, collection, getFirestore } from "firebase/firestore";
  const db = getFirestore(app);

  let count = 0;
  const increment = async () => {
    count += 1;
    try {
      const docRef = await addDoc(collection(db, "counts"), {
        date: new Date(),
        count,
      });
      console.log("Document written with ID: ", docRef.id);
    } catch (e) {
      console.error("Error adding document: ", e);
    }
  };
</script>

<button on:click={increment}>
  count is {count}
</button>
