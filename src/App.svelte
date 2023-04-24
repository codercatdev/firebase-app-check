<script>
  import LibLoader from "./lib/LibLoader.svelte";
  const onLoaded = () => {
    console.log("third party script loaded");
  };
  // @ts-ignore
  window.onloadCallback = () => {
    // @ts-ignore
    grecaptcha.render("html_element", {
      sitekey: "6LdbU7QlAAAAAFCxSSOngerVPcoZHknumevi7DEC",
    });
  };
</script>

<LibLoader
  url="https://www.google.com/recaptcha/api.js?onload=onloadCallback&render=explicit"
  on:loaded={onLoaded}
/>

<form action="?" method="POST">
  <div id="html_element" />
  <br />
  <input type="submit" value="Submit" />
</form>
