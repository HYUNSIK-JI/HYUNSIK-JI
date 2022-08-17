### Hi there 👋

<!--
**HYUNSIK-JI/HYUNSIK-JI** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.
Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
<h2>💻Study</h2>
    
<div style="text-align:center">    
  <img src="https://img.shields.io/badge/HTML5-red?style=flat-square&logo=html5&logoColor=white"/>
  <img src="https://img.shields.io/badge/CSS-orange?style=flat-square&logo=css3&logoColor=white"/>
  <img src="https://img.shields.io/badge/JAVASCRIPT-yellow?style=flat-square&logo=javascript&logoColor=white"/>
  <img src="https://img.shields.io/badge/Python-red?style=flat-square&logo=Pythont&logoColor=white"/>
  <img src="https://img.shields.io/badge/Unity-blue?style=flat-square&logo=Unityt&logoColor=white"/>
  <img src="https://img.shields.io/badge/Spring5-green?style=flat-square&logo=Spring5t&logoColor=white"/>
</div>

<h2>🥇algorithm</h2>

<div sytle="text-align:center">
    
  [![Solved.ac Profile](http://mazassumnida.wtf/api/v2/generate_badge?boj=wlgustlra)](https://solved.ac/wlgustlra/)
</div>

<h2>🎮 Stats </h2>

![HYUNSIK-JI github stats](https://github-readme-stats.vercel.app/api?username=HYUNSIK-JI&show_icons=true)
// By DipokalHHJ 2021

all_tier = ['Bronze', 'Silver', 'Gold', 'Platinum', 'Diamond', 'Ruby']
all_subtier = ['V', "IV", 'III', 'II', 'I']

// Solved AC 데이터 가져오기
async function getSolvedacUserData() {
    let response = await fetch("https://solved.ac/api/v3/user/show?handle=wlgustlra", {
        method: "GET",
        headers: {
            "Content-Type": "application/json"
        }
    });

    let data = await response.json();
    return data;
}

// Solved AC 데이터 적용하기
async function loadSolvedacUserData() {
    let data = await getSolvedacUserData();
    let calculateTier = await calculateSolvedacTier(data.tier);
    let count = document.querySelector('#totalSolvedCount');
    let tier = document.querySelector('#solvedTier');
    let maxstreak = document.querySelector('#solvedMaxStreak');

    count.innerHTML = `백준에서 푼 문제 수 <b class="text-primary">${data.solvedCount}</b>`;
    tier.innerHTML = `백준 티어 <b class="text-primary">${calculateTier}</b>`;
    maxstreak.innerHTML = `최대 연속 문제 풀이일 수 <b class="text-primary">${data.maxStreak}일</b>`;

}


// Solved AC 티어 계산
async function calculateSolvedacTier(idx) {
    let tier = 0
    let subtier = 0

    if (Number.isInteger(idx/5)) {
        tier = Math.floor(idx/5)-1
    } else {
        tier = Math.floor(idx/5)
    }

    if (idx%5 == 1) {
        subtier = 0
    }else if (idx%5 == 0) {
        subtier = 4
    } else {
        subtier = (idx%5)-1
    }

    return `${all_tier[tier]} ${all_subtier[subtier]}`
}
