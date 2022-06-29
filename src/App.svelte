<script>
  import "giscus";

  let youtubeLink = "";
  let youtubeLinkToMarkdownLinkFeedback = "";

  function youtubeLinkToMarkdownLink() {
    // https://www.youtube.com/watch?v=AjBediJpL3k
    let youtubeID = youtubeLink.match(/(?<=watch\?v=).*/);

    // for mobile share copy link
    if (!youtubeID) {
      youtubeLink.match(/(?<=youtube\.be\/).*/);
    }

    // TODO: shorts

    // [![](https://img.youtube.com/vi/LeVESAXm3U4/0.jpg)](https://www.youtube.com/watch?v=LeVESAXm3U4)
    let markdownString = `[![](https://img.youtube.com/vi/${youtubeID}/0.jpg)](https://www.youtube.com/watch?v=${youtubeID})`;

    navigator.clipboard.writeText(markdownString).then(
      function () {
        console.log("Async: Copying to clipboard was successful!");
        youtubeLinkToMarkdownLinkFeedback = "Copied to clipboard!";
        setTimeout(() => {
          youtubeLinkToMarkdownLinkFeedback = "";
        }, 2000);
      },
      function (err) {
        console.error("Async: Could not copy text: ", err);
      }
    );
  }
</script>

<main style="max-width: 80rem; margin: auto; padding: 1rem;">
  <span
    ><h1 style="display: inline; margin-right: 0.5rem;">vavava</h1>

    haki social media</span
  >
  <div style="text-align: center;">
    <!-- Paste a YouTube link for Markdown Formating, then press enter -->
    <input
      class="form-control input-contrast gsc-comment-box-textarea "
      type="text"
      placeholder="Format Youtube Link"
      bind:value={youtubeLink}
      on:keyup={(e) => {
        e.code == "Enter" && youtubeLinkToMarkdownLink();
      }}
    />
    <button
      class="ml-1 border rounded-md items-center btn btn-secondary"
      on:click={youtubeLinkToMarkdownLink}>Format</button
    >
    <p>{youtubeLinkToMarkdownLinkFeedback}</p>
  </div>

  <giscus-widget
    id="comments"
    repo="kimeiga/vavava"
    repoid="R_kgDOHk59og"
    category="General"
    categoryid="DIC_kwDOHk59os4CP7td"
    mapping="pathname"
    reactionsenabled="1"
    emitmetadata="1"
    inputposition="top"
    theme="preferred_color_scheme"
    lang="en"
    loading="lazy"
  />

  <!-- <img src={logo} alt="Svelte Logo" />
  <h1>Hello world!</h1>

  <Counter />

  <p>
    Visit <a href="https://svelte.dev">svelte.dev</a> to learn how to build Svelte
    apps.
  </p>

  <p>
    Check out <a href="https://github.com/sveltejs/kit#readme">SvelteKit</a> for
    the officially supported framework, also powered by Vite!
  </p> -->
</main>

<style>
  /* :root {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
      Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  }

  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
  }

  img {
    height: 16rem;
    width: 16rem;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4rem;
    font-weight: 100;
    line-height: 1.1;
    margin: 2rem auto;
    max-width: 14rem;
  }

  p {
    max-width: 14rem;
    margin: 1rem auto;
    line-height: 1.35;
  }

  @media (min-width: 480px) {
    h1 {
      max-width: none;
    }

    p {
      max-width: none;
    }
  } */
</style>
