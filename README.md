<!DOCTYPE html>
<html>
<head>
  <title>NearHelp Resource Finder</title>
  <style>
    body { font-family: Arial, sans-serif; }
    .resource { border: 1px solid #ccc; padding: 10px; margin: 10px 0; }
  </style>
</head>
<body>
  <h1>Find LGBTQ+ Resources Near You</h1>
  <label for="location">Select Location:</label>
  <select id="location">
    <option value="Thunder Bay">Thunder Bay</option>
    <option value="Toronto">Toronto</option>
  </select>

  <label for="type">Select Resource Type:</label>
  <select id="type">
    <option value="Therapy">Therapy</option>
    <option value="Hotline">Hotline</option>
    <option value="Support Group">Support Group</option>
  </select>

  <button onclick="findResources()">Search</button>

  <div id="results"></div>

  <script>
    const resources = [
      {
        name: "The Other 10%",
        location: "Thunder Bay",
        type: "Support Group",
        description: "A social group for 2SLGBTQ+ youth aged 12-25.",
        link: "https://www.rainbowcollectiveofthunderbay.com/services-2"
      },
      {
        name: "Thunder Bay Counselling",
        location: "Thunder Bay",
        type: "Therapy",
        description: "Walk-in counselling services on Wednesdays.",
        link: "https://www.rainbowhealthontario.ca/service-provider-directory/thunder-bay-counselling/"
      },
      {
        name: "Anishnawbe Mushkiki – Gender Journeys",
        location: "Thunder Bay",
        type: "Support Group",
        description: "8-week group exploring gender identity and roles.",
        link: "https://mushkiki.com/program/2slgbtiaq-healthcare/"
      },
      {
        name: "Supporting Our Youth (SOY)",
        location: "Toronto",
        type: "Support Group",
        description: "Drop-in groups for 2SLGBTQ+ youth.",
        link: "https://soytoronto.com/"
      },
      {
        name: "Friends of Ruby",
        location: "Toronto",
        type: "Therapy",
        description: "Free counselling and housing services for 2SLGBTQIA+ youth.",
        link: "https://www.friendsofruby.ca/"
      },
      {
        name: "Central Toronto Youth Services (CTYS)",
        location: "Toronto",
        type: "Therapy",
        description: "Counselling and support for LGBTQ+ youth and families.",
        link: "https://ctys.org/resources/2slgbtq-resources-services/"
      },
      {
        name: "LGBT YouthLine",
        location: "Ontario",
        type: "Hotline",
        description: "Confidential peer support for 2SLGBTQ+ youth.",
        link: "https://www.youthline.ca/"
      },
      {
        name: "Trans Lifeline",
        location: "Ontario",
        type: "Hotline",
        description: "Peer support hotline run by and for trans people.",
        link: "https://translifeline.org/"
      }
    ];

    function findResources() {
      const location = document.getElementById('location').value;
      const type = document.getElementById('type').value;
      const resultsDiv = document.getElementById('results');
      resultsDiv.innerHTML = '';

      const filtered = resources.filter(r => 
        (r.location === location || r.location === "Ontario") && r.type === type
      );

      if (filtered.length === 0) {
        resultsDiv.innerHTML = '<p>No resources found for your selection.</p>';
        return;
      }

      filtered.forEach(r => {
        const div = document.createElement('div');
        div.className = 'resource';
        div.innerHTML = `<h3>${r.name}</h3><p>${r.description}</p><a href="${r.link}" target="_blank">Learn More</a>`;
        resultsDiv.appendChild(div);
      });
    }
  </script>
</body>
</html>
