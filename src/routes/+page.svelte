<script>
  import { base } from '$app/paths';
  const isDev = import.meta.env.MODE === 'development';

  // News data for the "Show More" functionality
  let news = [
    { date: "24 October", text: "2 papers accepted at NeurIPS 2410!" },
    { date: "24 October", text: "2 papers submitted to ICLR 2410!" },
    { date: "24 September", text: "GAI successfully hosted the Graph Learning workshop." },
    { date: "24 August", text: "GAI researchers collaborate with OpenAI on graph models." },
    { date: "24 May", text: "Graph Augmented Intelligence (GAI) was established!" }
  ];

  // Publications and projects with placeholder data
  let publications = [
    {
      title: "Placeholder Publication 1",
      conference: "AMA Citation Example 1",
      awards: "Best Paper Award",
      links: { pdf: "#", code: "#", bibtex: "#", demo: "#", poster: "#" },
      image: isDev ? "/images/publication1.png" : `${base}/images/publication1.png`
    },
    {
      title: "Placeholder Publication 2",
      conference: "AMA Citation Example 2",
      awards: "Honorable Mention",
      links: { pdf: "#", code: "#", bibtex: "#", demo: "#", poster: "#" },
      image: isDev ? "/images/publication2.png" : `${base}/images/publication2.png`
    }
  ];

  let funProjects = [
    {
      title: "Placeholder Fun Project 1",
      description: "Description of the fun project.",
      stars: 50,
      codeLink: "#",
      image: isDev ? "/images/project1.gif" : `${base}/images/project1.gif`
    },
    {
      title: "Placeholder Fun Project 2",
      description: "Another fun project description.",
      stars: 30,
      codeLink: "#",
      image: isDev ? "/images/project2.gif" : `${base}/images/project2.gif`
    }
  ];

  // "Show More" logic for news
  let showMoreNews = false;
</script>

<main>
  <!-- Organization Section -->
  <section class="organization">
    <h1>Graph Augmented Intelligence (GAI)</h1>
    <img src={isDev ? "/images/gai-logo.png" : `${base}/images/gai-logo.png`} alt="GAI Logo" class="logo" />
    <p>We are a research organization focused on advancing AI for graph data structures. Our mission is to push the boundaries of graph-based learning algorithms and their applications in real-world systems.</p>
    <a class="button" href={`${base}/teams`}>Meet the Team</a>
    <a class="button" href="https://github.com/your-organization" target="_blank">GitHub</a>
  </section>

  <!-- News Section -->
  <section class="news">
    <h2>News</h2>
    <ul>
      {#each news.slice(0, showMoreNews ? news.length : 3) as item}
        <li>
          <strong>{item.date}</strong> - {item.text}
        </li>
      {/each}
    </ul>
    <button on:click={() => showMoreNews = !showMoreNews}>
      {showMoreNews ? "Show Less" : "Show More"}
    </button>
  </section>

  <!-- Featured Publications Section -->
  <section class="publications">
    <h2>Featured Publications</h2>
    {#each publications as pub}
      <div class="publication card">
        <div class="row">
          <img src={pub.image} alt={pub.title} class="publication-image" />
          <div class="details">
            <h3>{pub.title}</h3>
            <p>{pub.conference}</p>
            <p><strong>{pub.awards}</strong></p>
            <div class="links">
              <a href={pub.links.pdf}>PDF</a>
              <a href={pub.links.code}>Code</a>
              <a href={pub.links.bibtex}>BibTeX</a>
              <a href={pub.links.demo}>Demo</a>
              <a href={pub.links.poster}>Poster</a>
            </div>
          </div>
        </div>
      </div>
    {/each}
    <a class="button" href={`${base}/publications`}>See More</a>
  </section>

  <!-- Fun Projects Section -->
  <section class="projects">
    <h2>Fun Projects</h2>
    {#each funProjects as project}
      <div class="project card">
        <div class="row">
          <img src={project.image} alt={project.title} class="project-image" />
          <div class="details">
            <h3>{project.title}</h3>
            <p>{project.description}</p>
            <a class="button" href={project.codeLink}>View Code</a>
            <p>⭐ {project.stars} stars</p>
          </div>
        </div>
      </div>
    {/each}
    <a class="button" href={`${base}/projects`}>See More</a>
  </section>
</main>

<style>
  main {
    font-family: sans-serif;
    margin: 0 auto;
    max-width: 960px;
    background-color: #f8f9fa;
    padding: 20px;
  }

  /* Organization Section */
  .organization {
    text-align: center;
    margin-bottom: 2rem;
  }

  .logo {
    width: 200px;
    margin-bottom: 1rem;
  }

  .button {
    background-color: #ff7f0e;
    color: white;
    padding: 10px 15px;
    border-radius: 5px;
    text-decoration: none;
    margin: 0 10px;
  }

  .button:hover {
    background-color: #e0680d;
  }

  /* Row-wise layout for Publications and Projects */
  .row {
    display: flex;
    align-items: center;
    margin-bottom: 20px;
  }

  .publication-image, .project-image {
    width: 150px;
    height: auto;
    border-radius: 8px;
    margin-right: 20px;
  }

  .details {
    flex: 1;
  }

  .publication h3, .project h3 {
    margin: 0 0 0.5rem 0;
    color: #333;
  }

  /* Card Styles */
  .card {
    background: #ffe082; /* Restore background color */
    padding: 15px;
    border-radius: 8px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
    margin-bottom: 20px;
  }

  /* News Section */
  .news ul {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  .news li {
    background: #e0f7fa;
    padding: 10px;
    border-radius: 8px;
    margin-bottom: 10px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
  }

  /* Buttons or interactive elements */
  .links a, .button {
    margin-right: 10px;
    display: inline-block;
  }
</style>
