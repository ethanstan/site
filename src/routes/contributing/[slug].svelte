<script>
  const QUERY = `
		query {
			contribute(slug: "${QUERYPARAMS["slug"]}") {
        title
				slug
				html
			}
		}
	`;
  const QUERYRES = {};

  const QUERYPARAMOPTS = `
		query {
			contributes {
				slug
			}
		}
	`;

  import Nav from "../../components/Nav.svelte";
  import Footer from "../../components/Footer.svelte";
  import ContributingList from "../../components/ContributingList.svelte";
</script>

<style>
  .title {
    font-size: 2.6em;
    font-weight: 500;
    margin-bottom: 1rem;
  }
  .content :global(h2) {
    font-size: 1.6em;
	font-weight: 500;
	margin-bottom: 0.5rem;
  }
  .content :global(pre) {
    background-color: #f9f9f9;
    box-shadow: inset 1px 1px 5px rgba(0, 0, 0, 0.05);
    padding: 0.5em;
    border-radius: 2px;
    overflow-x: auto;
  }
  .content :global(pre) :global(code) {
    background-color: transparent;
    padding: 0;
  }
  .content :global(ul) {
	line-height: 1.5;
	list-style: disc inside;
  }
  .content :global(li) {
    margin: 0 0 0.5em 0;
  }
  .content :global(a) {
	color: rgb(70,170,86);
	text-decoration: non;
  }

  .content :global(a:hover) {
	text-decoration: underline;
  }

  .content :global(code) {
	  background: #f4f4f4;
    border: 1px solid #ddd;
    border-left: 3px solid rgb(70,170,86);
    color: #666;
    font-family: monospace;
    line-height: 1.6;
    max-width: 100%;
    overflow: auto;
	  padding: 1em 1.5em;
	  margin: 1em 0;
    display: block;
    word-wrap: break-word;
    white-space: pre;
  }
</style>

<svelte:head>
  <title>{QUERYRES.contribute.title} - Contributing - JungleJS</title>
</svelte:head>

<Nav page={QUERYRES.contribute.slug} />

<main class="flex flex-col sm:flex-row sm:px-16 lg:px-32">
  <ContributingList page="/contributing/{QUERYRES.contribute.slug}" />
  <div class="content mt-5 sm:px-16 lg:px-32 text-left">
    <h1 class="title">{QUERYRES.contribute.title}</h1>

	{@html QUERYRES.contribute.html}
  </div>
</main>

<Footer />
