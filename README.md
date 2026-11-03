set -e

# Verify repository
git rev-parse --is-inside-work-tree >/dev/null
git remote get-url origin >/dev/null

# Create workflow directory
mkdir -p .github/workflows

# ==========================================
# COMPLETE GITHUB PROFILE README
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
- 💻 Developing backend applications and intelligent systems.
- 🧠 Exploring LLMs, RAG, Computer Vision and workflow orchestration.
- 🚀 Interested in building scalable, real-world software solutions.
- 🧩 Solved **180+ LeetCode problems**.

---

## 🛠️ Technologies & Tools

### Programming Languages

<p>
<img src="https://skillicons.dev/icons?i=java,python,cpp,c"/>
</p>

### AI / ML

<p>
<img src="https://skillicons.dev/icons?i=pytorch,opencv"/>
</p>

`Machine Learning` · `Deep Learning` · `Computer Vision` · `RAG` · `LLMs` · `YOLO`

### Backend & Development

<p>
<img src="https://skillicons.dev/icons?i=spring,fastapi,react,mysql,docker,git,github"/>
</p>

`Temporal` · `REST APIs` · `Ollama` · `Maven`

### Development Tools

<p>
<img src="https://skillicons.dev/icons?i=idea,vscode,postman,linux"/>
</p>

---

## 🚀 Featured Projects

| Project | Description | Tech Stack |
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

## 📊 GitHub Overview

<div align="center">

<a href="https://github.com/gouthamsukamanchi-ship-it">
<img src="https://img.shields.io/badge/GitHub-gouthamsukamanchi--ship--it-181717?style=for-the-badge&logo=github"/>
</a>

<br/><br/>

<img src="https://img.shields.io/github/followers/gouthamsukamanchi-ship-it?label=Followers&style=for-the-badge&logo=github&color=blue"/>
<img src="https://img.shields.io/github/stars/gouthamsukamanchi-ship-it?label=Profile%20Repo%20Stars&style=for-the-badge&logo=github&color=yellow"/>
<img src="https://img.shields.io/github/last-commit/gouthamsukamanchi-ship-it/gouthamsukamanchi-ship-it?style=for-the-badge&logo=github"/>

<br/><br/>

<img width="60%" src="https://streak-stats.demolab.com?user=gouthamsukamanchi-ship-it&theme=tokyonight&hide_border=true" alt="GitHub Streak"/>

</div>

---

## 🐍 Watch My Contributions Get Eaten!

<div align="center">

<img src="https://raw.githubusercontent.com/gouthamsukamanchi-ship-it/gouthamsukamanchi-ship-it/output/github-contribution-grid-snake-dark.svg" width="100%" alt="Contribution Snake"/>

</div>

---

## 🤝 Connect With Me

<div align="center">

<a href="https://github.com/gouthamsukamanchi-ship-it">
<img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white"/>
</a>

</div>

---

<div align="center">

### 💡 Building today what inspires tomorrow.

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:141E30,50:243B55,100:00C6FF&height=110&section=footer" width="100%"/>

</div>
EOF

# ==========================================
# CONTRIBUTION SNAKE AUTOMATION
# ==========================================

cat > .github/workflows/snake.yml <<'EOF'
name: Generate Contribution Snake

on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch:
  push:
    branches:
      - main

permissions:
  contents: write

jobs:
  generate:
    runs-on: ubuntu-latest

    steps:
      - name: Generate contribution snake
        uses: Platane/snk@v3
        with:
          github_user_name: gouthamsukamanchi-ship-it
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark

      - name: Publish snake to output branch
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

if ! git diff --cached --quiet; then
    git commit -m "docs: create complete animated GitHub profile"
else
    echo "No new changes to commit."
fi

git push -u origin main

echo ""
echo "=========================================="
echo " README AND SNAKE WORKFLOW PUSHED!"
echo "=========================================="
echo "Next: Open GitHub Actions and run Generate Contribution Snake."
