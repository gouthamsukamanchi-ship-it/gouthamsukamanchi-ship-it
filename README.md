set -e

mkdir -p .github/workflows

# Remove old snake workflow files
rm -f .github/workflows/snake.yml
rm -f .github/workflows/snake.yaml

# ==========================================
# COMPLETE PROFILE README
# ==========================================

cat > README.md <<'EOF'
<div align="center">

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:141E30,50:243B55,100:00C6FF&height=220&section=header&text=Goutham%20Sukamanchi&fontSize=45&fontColor=ffffff&animation=fadeIn&fontAlignY=35&desc=AI%20%7C%20ML%20%7C%20Backend%20Developer&descSize=18&descAlignY=55"/>

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=500&size=21&pause=1000&color=00C6FF&center=true&vCenter=true&width=700&lines=Computer+Science+Engineering+Student;AI+%2F+ML+Enthusiast;Backend+Developer;Building+Intelligent+Solutions"/>

<br/>

<img src="https://img.shields.io/badge/Focus-Artificial%20Intelligence-00C6FF?style=for-the-badge"/>
<img src="https://img.shields.io/badge/University-UPES-blue?style=for-the-badge"/>
<img src="https://img.shields.io/badge/Location-India-orange?style=for-the-badge"/>

</div>

---

## 👨‍💻 About Me

- 🎓 Computer Science Engineering student at **UPES, Dehradun**.
- 🤖 Passionate about Artificial Intelligence, Machine Learning and Deep Learning.
- 💻 Building backend applications and intelligent systems.
- 🧠 Exploring LLMs, RAG, Computer Vision and workflow orchestration.
- 🚀 Interested in scalable, real-world software solutions.
- 🧩 Solved **180+ LeetCode problems**.

---

## 🛠️ Tech Stack

**Languages**

<p>
<img src="https://skillicons.dev/icons?i=java,python,cpp,c"/>
</p>

**AI / ML**

<p>
<img src="https://skillicons.dev/icons?i=pytorch,opencv"/>
</p>

`Machine Learning` · `Deep Learning` · `Computer Vision` · `RAG` · `LLMs` · `YOLO`

**Backend & Development**

<p>
<img src="https://skillicons.dev/icons?i=spring,fastapi,react,mysql,docker,git,github"/>
</p>

`Temporal` · `REST APIs` · `Ollama` · `Maven`

**Tools**

<p>
<img src="https://skillicons.dev/icons?i=idea,vscode,postman,linux"/>
</p>

---

## 🚀 Featured Projects

| Project | Description | Technologies |
|---|---|---|
| **AeroSaga – Drone Mission Control** | Drone mission orchestration and workflow management | Java, Spring Boot, Temporal |
| **CodeMind** | AI coding assistant using Retrieval-Augmented Generation | Java, Spring Boot, RAG |
| **Driver Drowsiness Detection** | Real-time driver drowsiness and distraction monitoring | Java, OpenCV |
| **AI Face Recognition Attendance** | Automated face recognition attendance system | Python, OpenCV |
| **APIx – Airfare Price Index** | Real-time airfare price analysis | Python, APIs |

---

## 🏆 Achievements

- 🏅 Smart India Hackathon 2026 – Finalist.
- 🏅 IBM NH26 Hackathon – Finalist.
- ✈️ All India Aero Expo 2025, IIT Roorkee – 4th Rank.
- 💻 180+ LeetCode problems solved.

---

## 📊 GitHub Statistics

<div align="center">

<img src="https://img.shields.io/github/followers/gouthamsukamanchi-ship-it?style=for-the-badge&logo=github&label=Followers"/>
<img src="https://img.shields.io/github/stars/gouthamsukamanchi-ship-it/gouthamsukamanchi-ship-it?style=for-the-badge&logo=github&label=Profile%20Stars"/>

<br/><br/>

<img width="60%" src="https://streak-stats.demolab.com?user=gouthamsukamanchi-ship-it&theme=tokyonight&hide_border=true" alt="GitHub Streak"/>

</div>

---

## 🐍 Watch My Contributions Get Eaten!

<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/gouthamsukamanchi-ship-it/gouthamsukamanchi-ship-it/output/github-snake-dark.svg"/>
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/gouthamsukamanchi-ship-it/gouthamsukamanchi-ship-it/output/github-snake.svg"/>
  <img alt="GitHub Contribution Snake" src="https://raw.githubusercontent.com/gouthamsukamanchi-ship-it/gouthamsukamanchi-ship-it/output/github-snake.svg" width="100%"/>
</picture>

</div>

---

## 🤝 Connect With Me

<div align="center">

<a href="https://github.com/gouthamsukamanchi-ship-it">
<img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white"/>
</a>

</div>

<div align="center">

### 💡 Building today what inspires tomorrow.

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:141E30,50:243B55,100:00C6FF&height=110&section=footer"/>

</div>
EOF

# ==========================================
# NEW SNAKE GENERATOR WORKFLOW
# ==========================================

cat > .github/workflows/snake.yml <<'EOF'
name: Generate Contribution Snake

on:
  workflow_dispatch:
  schedule:
    - cron: "0 0 * * *"
  push:
    branches:
      - main

permissions:
  contents: write

jobs:
  generate:
    runs-on: ubuntu-latest

    steps:
      - name: Generate snake SVG files
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: gouthamsukamanchi-ship-it
          outputs: |
            dist/github-snake.svg
            dist/github-snake-dark.svg?palette=github-dark

      - name: Publish generated SVG files
        uses: peaceiris/actions-gh-pages@v4
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
          publish_branch: output
          force_orphan: true
EOF

# ==========================================
# COMMIT AND PUSH
# ==========================================

git add README.md .github/workflows/snake.yml

git commit -m "docs: update profile README and contribution animation"

git push origin main

echo ""
echo "SUCCESS: README and new snake workflow pushed!"
echo "Next: Enable GitHub Actions read/write permissions."
