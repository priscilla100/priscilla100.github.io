<h1 id="work-experience"></h1>

<h2 style="margin: 60px 0px 15px;">Work Experience</h2>

<div class="work-experience">
  <ul style="list-style-type: none; padding-left: 0;">

    {% for job in site.data.work_experience.work_experience %}
    <li style="margin-bottom: 30px;">
      <div>
        <h3 style="margin-bottom: 5px;">{{ job.position }}</h3>
        <p style="margin: 0; font-size: 16px; color: #555;">
          <strong>{{ job.company }}</strong> | {{ job.location }} | {{ job.start_date }} - {{ job.end_date }}
        </p>
        <ul style="list-style-type: disc; padding-left: 40px; margin-top: 10px;">
          {% for item in job.description %}
          <li style="margin-bottom: 5px;">{{ item }}</li>
          {% endfor %}
        </ul>
        <p style="margin: 10px 0 0; font-size: 14px; color: #777;">
          <strong>Skills:</strong> {{ job.skills | join: ", " }}
        </p>
      </div>
    </li>
    {% endfor %}

  </ul>
</div>