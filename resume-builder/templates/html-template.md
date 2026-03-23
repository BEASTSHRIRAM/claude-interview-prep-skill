# HTML + CSS Resume Template

Use this template when the student chooses Option 1 (HTML/CSS visual resume).
Replace all placeholder values with the student's actual details.
Deliver BOTH the HTML and CSS code blocks separately so they can save as index.html and index.css.

---

## index.html

```html
<!DOCTYPE html>
<html>
<head>
  <link href="https://maxcdn.bootstrapcdn.com/font-awesome/4.2.0/css/font-awesome.min.css" rel="stylesheet">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Archivo+Narrow&family=Julius+Sans+One&family=Open+Sans&family=Source+Sans+Pro&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="index.css">
</head>
<body>
  <page size="A4">
    <div class="container">
      <div class="leftPanel">
        <div class="details">
          <div class="item bottomLineSeparator">
            <h2>CONTACT</h2>
            <div class="smallText">
              <p>
                <i class="fa fa-phone contactIcon" aria-hidden="true"></i>
                {{PHONE}}
              </p>
              <p>
                <i class="fa fa-envelope contactIcon" aria-hidden="true"></i>
                <a href="mailto:{{EMAIL}}">{{EMAIL}}</a>
              </p>
              <p>
                <i class="fa fa-map-marker contactIcon" aria-hidden="true"></i>
                {{CITY}}, {{STATE}}
              </p>
              <p>
                <i class="fa fa-linkedin-square contactIcon" aria-hidden="true"></i>
                <a href="{{LINKEDIN_URL}}">{{LINKEDIN_HANDLE}}</a>
              </p>
              <p class="lastParagrafNoMarginBottom">
                <i class="fa fa-github contactIcon" aria-hidden="true"></i>
                <a href="{{GITHUB_URL}}">{{GITHUB_HANDLE}}</a>
              </p>
            </div>
          </div>

          <div class="item bottomLineSeparator">
            <h2>SKILLS</h2>
            <div class="smallText">
              <!-- LANGUAGES -->
              <p class="bolded white">Languages</p>
              <p>{{LANGUAGES}}</p>

              <!-- FRAMEWORKS -->
              <p class="bolded white">Frameworks</p>
              <p>{{FRAMEWORKS}}</p>

              <!-- DATABASES -->
              <p class="bolded white">Databases</p>
              <p>{{DATABASES}}</p>

              <!-- TOOLS -->
              <p class="bolded white">Tools</p>
              <p>{{TOOLS}}</p>
            </div>
          </div>

          <div class="item bottomLineSeparator">
            <h2>EDUCATION</h2>
            <div class="smallText">
              <p class="bolded white">{{DEGREE}}</p>
              <p>{{COLLEGE}}</p>
              <p>{{GRAD_YEAR_START}} - {{GRAD_YEAR_END}}</p>
              <p>CGPA: {{CGPA}}</p>
            </div>
          </div>

          <!-- ACHIEVEMENTS SECTION (remove if none) -->
          <div class="item">
            <h2>ACHIEVEMENTS</h2>
            <div class="smallText">
              <ul>
                <li>{{ACHIEVEMENT_1}}</li>
                <li>{{ACHIEVEMENT_2}}</li>
                <li>{{ACHIEVEMENT_3}}</li>
              </ul>
            </div>
          </div>

        </div>
      </div>

      <div class="rightPanel">
        <div>
          <h1>{{FULL_NAME}}</h1>
          <div class="smallText">
            <h3>{{ROLE_OR_BRANCH}}</h3>
          </div>
        </div>

        <!-- ABOUT / SUMMARY (optional, remove if not needed) -->
        <div>
          <h2>Summary</h2>
          <div class="smallText">
            <p>{{SUMMARY_LINE}}</p>
          </div>
        </div>

        <!-- WORK EXPERIENCE (remove this entire section if no internship) -->
        <div class="workExperience">
          <h2>Experience</h2>
          <ul>
            <li>
              <div class="jobPosition">
                <span class="bolded">{{JOB_TITLE}}</span>
                <span>{{JOB_START}} - {{JOB_END}}</span>
              </div>
              <div class="projectName bolded">
                <span>{{COMPANY_NAME}}</span>
              </div>
              <div class="smallText">
                <ul>
                  <li>{{JOB_BULLET_1}}</li>
                  <li>{{JOB_BULLET_2}}</li>
                  <li>{{JOB_BULLET_3}}</li>
                </ul>
                <p><span class="bolded">Skills: </span>{{JOB_SKILLS}}</p>
              </div>
            </li>
          </ul>
        </div>

        <!-- PROJECTS -->
        <div class="workExperience">
          <h2>Projects</h2>
          <ul>
            <li>
              <div class="jobPosition">
                <span class="bolded">{{PROJECT_1_NAME}}</span>
                <span>{{PROJECT_1_DATE}}</span>
              </div>
              <div class="projectName bolded">
                <span>{{PROJECT_1_TECH_STACK}}</span>
              </div>
              <div class="smallText">
                <ul>
                  <li>{{PROJECT_1_BULLET_1}}</li>
                  <li>{{PROJECT_1_BULLET_2}}</li>
                  <li>{{PROJECT_1_BULLET_3}}</li>
                </ul>
              </div>
            </li>

            <li>
              <div class="jobPosition">
                <span class="bolded">{{PROJECT_2_NAME}}</span>
                <span>{{PROJECT_2_DATE}}</span>
              </div>
              <div class="projectName bolded">
                <span>{{PROJECT_2_TECH_STACK}}</span>
              </div>
              <div class="smallText">
                <ul>
                  <li>{{PROJECT_2_BULLET_1}}</li>
                  <li>{{PROJECT_2_BULLET_2}}</li>
                  <li>{{PROJECT_2_BULLET_3}}</li>
                </ul>
              </div>
            </li>
          </ul>
        </div>

      </div>
    </div>
  </page>
</body>
</html>
```

---

## index.css

```css
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

page {
  background: white;
  display: block;
  margin: 0 auto;
  margin-bottom: 0.5cm;
  box-shadow: 0 4px 5px rgba(75, 75, 75, 0.2);
}

page[size="A4"] {
  width: 21cm;
  height: 29.7cm;
  overflow: hidden;
}

.container {
  display: flex;
  flex-direction: row;
  height: 100%;
}

.leftPanel {
  width: 27%;
  background-color: #484444;
  padding: 0.7cm 0.5cm;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.leftPanel img {
  width: 3.5cm;
  height: 3.5cm;
  border-radius: 50%;
  object-fit: cover;
  margin-bottom: 0.5cm;
  border: 3px solid white;
}

.details {
  width: 100%;
}

.item {
  padding: 0.3cm 0;
  color: rgba(255, 255, 255, 0.85);
}

.bottomLineSeparator {
  border-bottom: 0.5px solid rgba(255, 255, 255, 0.3);
  margin-bottom: 0.2cm;
}

.item h2 {
  font-family: 'Julius Sans One', sans-serif;
  font-size: 0.4cm;
  letter-spacing: 0.15cm;
  color: white;
  margin-bottom: 0.25cm;
}

.smallText {
  font-family: 'Source Sans Pro', sans-serif;
  font-size: 0.32cm;
  line-height: 1.5;
}

.smallText p {
  margin-bottom: 0.15cm;
}

.smallText a {
  color: rgba(255, 255, 255, 0.85);
  text-decoration: none;
}

.smallText a:hover {
  color: white;
  text-decoration: underline;
}

.contactIcon {
  margin-right: 0.2cm;
  color: rgba(255, 255, 255, 0.7);
}

.lastParagrafNoMarginBottom {
  margin-bottom: 0 !important;
}

.bolded {
  font-weight: bold;
}

.white {
  color: white;
}

.skill {
  display: flex;
  justify-content: space-between;
  margin-bottom: 0.1cm;
  color: rgba(255, 255, 255, 0.85);
}

.rightPanel {
  width: 73%;
  padding: 0.7cm 0.7cm;
  display: flex;
  flex-direction: column;
  gap: 0.3cm;
}

.rightPanel h1 {
  font-family: 'Julius Sans One', sans-serif;
  font-size: 0.9cm;
  color: #484444;
  letter-spacing: 0.05cm;
}

.rightPanel h2 {
  font-family: 'Julius Sans One', sans-serif;
  font-size: 0.4cm;
  letter-spacing: 0.1cm;
  color: #484444;
  border-bottom: 1px solid #484444;
  padding-bottom: 0.1cm;
  margin-bottom: 0.2cm;
}

.rightPanel h3 {
  font-family: 'Archivo Narrow', sans-serif;
  font-size: 0.42cm;
  color: #777;
  font-weight: normal;
  margin-top: 0.05cm;
}

.rightPanel .smallText {
  color: #444;
  font-size: 0.33cm;
}

.workExperience ul {
  list-style: none;
  padding: 0;
}

.workExperience ul li {
  margin-bottom: 0.3cm;
}

.jobPosition {
  display: flex;
  justify-content: space-between;
  font-size: 0.35cm;
  color: #333;
}

.projectName {
  font-size: 0.33cm;
  color: #555;
  margin: 0.05cm 0;
}

.workExperience .smallText ul {
  list-style: disc;
  padding-left: 0.4cm;
  margin: 0.1cm 0;
}

.workExperience .smallText ul li {
  margin-bottom: 0.08cm;
  color: #555;
}

@media print {
  body {
    margin: 0;
  }
  page {
    box-shadow: none;
    margin: 0;
  }
}
```

---

## Instructions to give the student

1. Save the HTML code as `index.html`
2. Save the CSS code as `index.css` in the same folder
3. Open `index.html` in any browser
4. To export as PDF: press `Ctrl+P` (or `Cmd+P` on Mac), set destination to "Save as PDF", set margins to "None", enable "Background graphics"
5. To add a profile photo: save your image as `avatar.png` in the same folder and add `<img src="avatar.png"/>` inside `.leftPanel` before `.details`
