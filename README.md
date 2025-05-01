[![Typing SVG](https://readme-typing-svg.demolab.com?font=Long+Cang&weight=500&size=30&pause=1000&center=true&vCenter=true&width=444&height=73&lines=%E5%B8%8C%E6%9C%9B%E4%BD%A0%E8%83%BD%E5%9C%A8%E8%87%AA%E5%B7%B1%E7%9A%84%E8%B7%AF%E4%B8%8A%E5%8E%BB%E5%A5%8B%E6%96%97%EF%BC%81)](https://git.io/typing-svg)

## Hello everyone, I am EchoCax !👋
### 


<h2>正在学习：</h2>
<img src="https://img.shields.io/badge/-HTML5-E34F26?style=flat-square&logo=html5&logoColor=white" /> <img src="https://img.shields.io/badge/-CSS3-1572B6?style=flat-square&logo=css3" /> <img src="https://img.shields.io/badge/-JavaScript-oringe?style=flat-square&logo=javascript" /> </span>

[![Ashutosh's github activity graph](https://github-readme-activity-graph.vercel.app/graph?username=EchoCax&bg_color=ccb9f9&color=210908&line=ce78ce&point=e85959&area=true&hide_border=true)](https://github.com/ashutosh00710/github-readme-activity-graph)

![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=EchoCax&layout=compact&theme=tokyonight)

name: generate animation

on:
  # run automatically every 2 hours
  schedule:
    - cron: "0 */2 * * *" 
  
  # allows to manually run the job at any time
  workflow_dispatch:
  
  # run on every push on the master branch
  push:
    branches:
    - master
  
  

jobs:
  generate:
    permissions: 
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5
  
    steps:
      # generates a snake game from a github user (EchoCax) contributions graph, output a svg animation at <svg_out_path>
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          EchoCax: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
  
  
      # push the content of <build_dir> to a branch
      # the content will be available at https://raw.githubusercontent.com/<github_user>/<repository>/<target_branch>/<file> , or as github page
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
