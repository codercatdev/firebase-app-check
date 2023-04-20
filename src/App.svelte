<script>
  import Firebase_Logo_Logomark from "./assets/Firebase_Logo_Logomark.svg";
  import ReCaptcha from "./assets/recaptcha_48dp.png";
  import { initializeApp } from "firebase/app";
  import Counter from "./lib/Counter.svelte";
  import CounterReader from "./lib/CounterReader.svelte";

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

  // reCAPTCHA App Check

  import { initializeAppCheck, ReCaptchaV3Provider } from "firebase/app-check";

  if (import.meta.env.DEV) {
    // @ts-ignore
    self.FIREBASE_APPCHECK_DEBUG_TOKEN = true;
  }

  initializeAppCheck(app, {
    provider: new ReCaptchaV3Provider(
      "6LdAIqQlAAAAAC4kq-bag4J-HmAAVe_pu7T75QOf"
    ),
    isTokenAutoRefreshEnabled: true,
  });
</script>

<main>
  <div>
    <a href="https://firebase.google.com" target="_blank" rel="noreferrer">
      <img
        src={Firebase_Logo_Logomark}
        class="logo firebase"
        alt="Firebase Logo"
      />
    </a>
    <a
      href="https://developers.google.com/recaptcha"
      target="_blank"
      rel="noreferrer"
    >
      <img src={ReCaptcha} class="logo" alt="Recaptcha Logo" />
    </a>
  </div>
  <h1>Firebase with App Check (using reCAPTCHA)</h1>

  <div class="card">
    <Counter {app} />
    <CounterReader {app} />
  </div>

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
  .logo.firebase:hover {
    filter: drop-shadow(0 0 2em #ffea00fb);
  }
</style>
