<script>
  import Firebase_Logo_Logomark from "./assets/Firebase_Logo_Logomark.svg";
  import { initializeApp } from "firebase/app";
  import { getFirestore } from "firebase/firestore";

  const firebaseConfig = {
    apiKey: "AIzaSyAH2JT998LjBxxJO0eX_V5LPAyhhxV2fQQ",
    authDomain: "ccd-firebase-app-check.firebaseapp.com",
    projectId: "ccd-firebase-app-check",
    storageBucket: "ccd-firebase-app-check.appspot.com",
    messagingSenderId: "566747634816",
    appId: "1:566747634816:web:fec9bcaf25c950d0995a65",
  };

  // Initialize Firebase
  const app = initializeApp(firebaseConfig);
  const db = getFirestore(app);
</script>

<main>
  <div>
    <a href="https://firebase.google.com" target="_blank" rel="noreferrer">
      <img src={Firebase_Logo_Logomark} class="logo" alt="Firebase Logo" />
    </a>
  </div>
  <h1>Firebase without App Check</h1>

  <div class="card" />

  <p>
    Check out <a
      href="https://firebase.google.com/docs/app-check"
      target="_blank"
      rel="noreferrer">Firebase App Check</a
    >
  </p>
</main>

<style>
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
  .read-the-docs {
    color: #888;
  }
</style>
