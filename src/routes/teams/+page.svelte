<script>
  import { base } from '$app/paths';
  const isDev = import.meta.env.MODE === 'development';

  let teamMembers = [
    {
      name: "Team Member 1",
      affiliation: "Affiliation 1",
      image: isDev ? "/images/team1.png" : `${base}/images/team1.png`,
      github: "https://github.com/team1",
      googleScholar: "https://scholar.google.com/team1",
      linkedin: "https://linkedin.com/in/team1"
    },
    {
      name: "Team Member 2",
      affiliation: "Affiliation 2",
      image: isDev ? "/images/team2.png" : `${base}/images/team2.png`,
      github: "https://github.com/team2",
      googleScholar: "https://scholar.google.com/team2",
      linkedin: "https://linkedin.com/in/team2"
    }
  ];
</script>

<main>
  <h1>Our Team</h1>
  <div class="team-grid">
    {#each teamMembers as member}
      <div class="team-member">
        <img src={member.image} alt={member.name} />
        <h3>{member.name}</h3>
        <p>{member.affiliation}</p>
        <div class="links">
          <a href={member.github} target="_blank" rel="noopener noreferrer">
            <img src={isDev ? "/images/github-icon.png" : `${base}/images/github-icon.png`} alt="GitHub" class="icon" />
          </a>
          <a href={member.googleScholar} target="_blank" rel="noopener noreferrer">
            <img src={isDev ? "/images/google-scholar-icon.png" : `${base}/images/google-scholar-icon.png`} alt="Google Scholar" class="icon" />
          </a>
          <a href={member.linkedin} target="_blank" rel="noopener noreferrer">
            <img src={isDev ? "/images/linkedin-icon.png" : `${base}/images/linkedin-icon.png`} alt="LinkedIn" class="icon" />
          </a>
        </div>
      </div>
    {/each}
  </div>
</main>

<style>
  main {
    font-family: sans-serif;
    padding: 20px;
  }

  .team-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 20px;
  }

  .team-member {
    text-align: center;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 8px;
  }

  .team-member img {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    margin-bottom: 10px;
  }

  .links {
    margin-top: 10px;
  }

  .links a {
    margin-right: 10px;
  }

  .icon {
    width: 24px;
    height: 24px;
  }
</style>
