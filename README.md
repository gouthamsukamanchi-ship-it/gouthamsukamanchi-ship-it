mkdir -p .github/workflows

cat > README.md <<'EOF'
<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&height=220&color=0:000428,50:004e92,100:00c6ff&text=Goutham%20Sukamanchi&fontSize=45&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=AI%20%7C%20ML%20%7C%20Backend%20Developer&descAlignY=58&descSize=18" width="100%"/>

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=500&size=22&pause=1000&color=00C6FF&center=true&vCenter=true&width=700&lines=Computer+Science+Engineering+Student;AI+%2F+ML+Enthusiast;Backend+Developer;Building+Intelligent+Real-World+Solutions" />

</div>

---

## 👨‍💻 About Me

- 🎓 Computer Science Engineering student at **UPES, Dehradun**.
- 🤖 Interested in Artificial Intelligence, Machine Learning and Deep Learning.
- 💻 Building backend systems and intelligent applications.
- 🚀 Exploring RAG, LLMs, Computer Vision and workflow orchestration.
- 🏆 SIH 2026 Finalist.
- 🥇 IBM NH26 Hackathon Finalist.
- ✈️ 4th Rank – All India Aero Expo 2025, IIT Roorkee.
- 🧩 180+ LeetCode problems solved.

---

## 🛠️ Tech Stack

### Programming Languages
<p>
<img src="https://skillicons.dev/icons?i=java,python,cpp,c" />
</p>

### AI / ML & Data Science
<p>
<img src="https://skillicons.dev/icons?i=pytorch,opencv" />
</p>

`Machine Learning` `Deep Learning` `Computer Vision` `RAG` `LLMs` `YOLO`

### Backend & Development
<p>
<img src="https://skillicons.dev/icons?i=spring,fastapi,react,mysql,docker,git,github" />
</p>

`Temporal` `REST APIs` `Ollama`

### Tools & Platforms
<p>
<img src="https://skillicons.dev/icons?i=linux,idea,vscode,postman,maven` />
</p>

---

## 🚀 Featured Projects

| Project | Description | Technologies |
|---|---|---|
| **AeroSaga – Drone Mission Control** | Drone mission orchestration and workflow management | Java, Spring Boot, Temporal |
| **CodeMind** | AI-powered coding assistant using RAG | Java, Spring Boot, RAG |
| **Driver Drowsiness Detection** | Real-time driver monitoring and distraction detection | Java, OpenCV |
| **Face Recognition Attendance** | AI-based face recognition attendance system | Python, OpenCV |
| **APIx – Airfare Price Index** | Real-time airfare price analysis | Python, APIs |

---

## 🏆 Achievements

- 🏅 Smart India Hackathon 2026 – Finalist.
- 🏅 IBM NH26 Hackathon – Finalist.
- ✈️ All India Aero Expo 2025, IIT Roorkee – 4th Rank.
- 💡 180+ LeetCode problems solved.

---

## 📊 GitHub Statistics

<p align="center">
  <img width="49%" src="https://github-readme-stats.vercel.app/api?username=gouthamsukamanchi-ship-it&show_icons=true&theme=tokyonight&hide_border=true&count_private=true" />
  <img width="49%" src="https://github-readme-stats.vercel.app/api/top-langs/?username=gouthamsukamanchi-ship-it&layout=compact&theme=tokyonight&hide_border=true" />
</p>

<p align="center">
  <img width="60%" src="https://streak-stats.demolab.com?user=gouthamsukamanchi-ship-it&theme=tokyonight&hide_border=true" />
</p>

---

## 🐍 Watch My Contributions Get Eaten!

<p align="center">
  <img src="https://raw.githubusercontent.com/gouthamsukamanchi-ship-it/gouthamsukamanchi-ship-it/output/github-contribution-grid-snake-dark.svg" width="100%" alt="Contribution Snake"/>
</p>

---

## 🤝 Connect With Me

<p align="center">
  <a href="https://github.com/gouthamsukamanchi-ship-it">
    <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white"/>
  </a>
</p>

<div align="center">

### 💡 "Building today what inspires tomorrow."

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:000428,50:004e92,100:00c6ff&height=100&section=footer" width="100%"/>

</div>
EOF

cat > .github/workflows/snake.yml <<'EOF'
name: Generate Contribution Snake

on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch:
  push:
    branches:
      - main

jobs:
  generate:
    runs-on: ubuntu-latest
    permissions:
      contents: write

    steps:
      - name: Generate Snake
        uses: Platane/snk@v3
        with:
          github_user_name: gouthamsukamanchi-ship-it
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark

      - name: Deploy Snake
        uses: peaceiris/actions-gh-pages@v4
        with:
          publish_dir: ./dist
          publish_branch: output
          github_token: ${{ secrets.GITHUB_TOKEN }}
EOF

git add README.md .github/workflows/snake.yml
git commit -m "docs: build animated GitHub profile README"
git push origin main
