<template>
  <div class="app-root">
    
    <div class="shortcut-bar-wrapper">
      <label id="s-bar-label">A M I R.</label>
      <ul id="shortcut-list">
        <li style="--list:1"><span><a style='text-decoration: none; color:inherit;' href='#home'>home</a></span></li>
        <li style="--list:2"><span><a style='text-decoration: none; color:inherit;' href='#about'>about</a></span></li>
        <li style="--list:3"><span><a style='text-decoration: none; color:inherit;' href='#experience'>experience</a></span></li>
        <li style="--list:4"><span><a style='text-decoration: none; color:inherit;' href='#portfolio'>portfolio</a></span></li>
      </ul>
    </div>

    <div id="home" ref="mainPageRef" class="main-page" :class="{ 'collapsed': !isHeaderExpanded }">
      <div class="media-wrapper">
        <div class="top-img-layout" :class="{ show: isHeaderExpanded }">
          <img src="/images/jp/PXL_20230908_044746576.jpg"/>
        </div>
        <div class="top-img-layout" :class="{ show: isHeaderExpanded }" style="transform: skewY(-10deg)">
          <img src="/images/jp/PXL_20230912_091805308.jpg" style="transform: skewY(10deg)"/>
        </div>
        <div class="top-img-layout" :class="{ show: isHeaderExpanded }">
          <img src="/images/jp/PXL_20230908_093228700.jpg"/>
        </div>
      </div>
      <section class="intro-wrapper">
        <h1>Amir Raif</h1>
        <p>> Software Engineer<span class="typewriter-effect"> {{ typewritereff }}</span></p>
      </section>
    </div>

    <svg style="background-color: white; margin-bottom: -10px; position:relative; z-index: 1;" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 320">
      <path fill="#000000" fill-opacity="1" d="M0,288L120,250.7C240,213,480,139,720,122.7C960,107,1200,149,1320,170.7L1440,192L1440,0L1320,0C1200,0,960,0,720,0C480,0,240,0,120,0L0,0Z"></path>
    </svg>

    <div id="about" ref="middleSectionRef" class="cinema-section" :class="{ 'reveal': isMiddleVisible }">
      <div class="cinema-wrapper">
        <div class="cinema-content">
          <div class="cinema-text">
            <h2>About Me</h2>
            <p>
              I am a Full Stack Developer with experience in RESTful APIs, NoSQL databases, and adaptive software development across
              multiple platforms. Experienced in building software and working with diverse languages and frameworks across
              various software development domains. Highly interested in the fintech industry, with a focus on investment-related
              solutions.
            </p>
            <div class="social">
              <a href="https://www.linkedin.com/in/amirraif/" target="_blank" class="linkedin-btn">
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" viewBox="0 0 16 16">
                  <path d="M0 1.146C0 .513.526 0 1.175 0h13.65C15.474 0 16 .513 16 1.146v13.708c0 .633-.526 1.146-1.175 1.146H1.175C.526 16 0 15.487 0 14.854V1.146zm4.943 12.248V6.169H2.542v7.225h2.401zm-1.2-8.212c.837 0 1.358-.554 1.358-1.248-.015-.709-.52-1.248-1.342-1.248-.822 0-1.359.54-1.359 1.248 0 .694.521 1.248 1.327 1.248h.015zm4.908 8.212V9.359c0-.216.016-.432.08-.586.173-.431.568-.878 1.232-.878.869 0 1.216.662 1.216 1.634v3.865h2.401V9.25c0-2.22-1.184-3.252-2.764-3.252-1.274 0-1.845.7-2.165 1.193v.025h-.016a5.54 5.54 0 0 1 .016-.025V6.169h-2.4c.03.678 0 7.225 0 7.225h2.4z"/>
                </svg>
                LinkedIn
              </a>
            </div>

          </div>
          <div class="cinema-img-box">
            <img src="/images/jp/PXL_20230910_032156807.jpg" alt="Profile"/>
          </div>
        </div>

        <div id="experience" class="experience-block">
          <div class="deck-title">Experience</div>

          <div class="exp-timeline">
            <div class="exp-row" v-for="(exp, i) in experiences" :key="i">
              <div class="exp-marker">
                <span class="exp-dot"></span>
                <span class="exp-line"></span>
              </div>
              <div class="exp-content">
                <span class="exp-period">{{ exp.period }}</span>
                <h3>{{ exp.role }}</h3>
                <h4>{{ exp.company }}</h4>
                <p>{{ exp.desc }}</p>
                <ul class="exp-highlights">
                  <li v-for="(point, j) in exp.highlights" :key="j">{{ point }}</li>
                </ul>
              </div>
            </div>
          </div>
        </div>

        <div class="project-deck">
          <div class="deck-title">Projects</div>
          
          <div class="p-row" v-for="(proj, i) in projects" :key="i" :class="{ 'reverse': i % 2 !== 0 }">
            
            <div class="p-visual">
              <div class="img-frame">
                <img :src="proj.image" alt="Project Image" />
              </div>
            </div>

            <div class="p-details">
              <span class="p-subtitle">{{ proj.subtitle }}</span>
              <h3>{{ proj.title }}</h3>
              <p>{{ proj.desc }}</p>
            </div>

          </div>
        </div>

      </div>
    </div>

    <div id="portfolio" ref="tertiarySectionRef" class="list-section" :class="{ 'reveal': isTertiaryVisible }">
      <div class="list-container">
        <div v-for="(item, index) in education" :key="index" class="list-row" :style="{ transitionDelay: `${index * 0.15}s` }">
          <div class="row-left">
            <h3>{{ item.institution }}</h3>
            <h4>{{ item.degree }}</h4>
          </div>
          <div class="row-right">
            <span>{{ item.meta }}</span>
          </div>
        </div>
        
        <div class="list-row link-row" :style="{ transitionDelay: '0.6s' }">
          <a href="https://github.com/SaitoGH" target="_blank">
            VIEW GITHUB REPOSITORIES <span class="arrow">&rarr;</span>
            <img src="https://github.com/SaitoGH.png" class="gh-profile-pic" alt="GH Profile" />
          </a>
        </div>
      </div>
    </div>

    <footer class="about-section">
      <img src="/images/logo/logo_w.png">
      <ul>
        <label>About</label>
        <li><a href="#about">about me</a></li>
        <li><a href="#experience">experience</a></li>
        <li><a href="#portfolio">studies</a></li>
        <li><a href="#portfolio">portfolio (projects)</a></li>
      </ul>

      <ul>
        <label>Get in touch</label>
        <li>
          <u><label>General Inquries</label></u><br><br>
          <a href="mailto:amirraifedu@gmail.com?subject=Feedback&body=Message">
            amirraifedu@gmail.com (gmail)
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-paperclip" viewBox="0 0 16 16">
              <path d="M4.5 3a2.5 2.5 0 0 1 5 0v9a1.5 1.5 0 0 1-3 0V5a.5.5 0 0 1 1 0v7a.5.5 0 0 0 1 0V3a1.5 1.5 0 1 0-3 0v9a2.5 2.5 0 0 0 5 0V5a.5.5 0 0 1 1 0v7a3.5 3.5 0 1 1-7 0z"/>
            </svg>
          </a>
        </li>
        <li>
          <u><label>Personal Inquries</label></u><br><br>
        </li>
        <li>
          <a target="_blank" href="https://github.com/SaitoGH">
            SaitoGH (github)
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-paperclip" viewBox="0 0 16 16">
              <path d="M4.5 3a2.5 2.5 0 0 1 5 0v9a1.5 1.5 0 0 1-3 0V5a.5.5 0 0 1 1 0v7a.5.5 0 0 0 1 0V3a1.5 1.5 0 1 0-3 0v9a2.5 2.5 0 0 0 5 0V5a.5.5 0 0 1 1 0v7a3.5 3.5 0 1 1-7 0z"/>
            </svg>
          </a>
        </li>
      </ul>
      <ul>
        <li>
          <u><label>Privacy & Policy</label></u><br><br>
          <a target="_blank" href="https://www.termsfeed.com/live/59d9d078-7ac0-46cf-9ff6-5026a9f1a92c">
            Amir Records Privacy Policy 
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-paperclip" viewBox="0 0 16 16">
              <path d="M4.5 3a2.5 2.5 0 0 1 5 0v9a1.5 1.5 0 0 1-3 0V5a.5.5 0 0 1 1 0v7a.5.5 0 0 0 1 0V3a1.5 1.5 0 1 0-3 0v9a2.5 2.5 0 0 0 5 0V5a.5.5 0 0 1 1 0v7a3.5 3.5 0 1 1-7 0z"/>
            </svg>
          </a>
        </li>
      </ul>
      <label id="tag">@AmirRecords 2022</label>
    </footer>

  </div>
</template>
<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

//typewriter effect ltierally just one thing lol
let typewritereff = ref('_');
window.setInterval(() => {
  typewritereff.value = typewritereff.value === '_' ? '' : '_';
}, 500);
const mainPageRef = ref(null);
const middleSectionRef = ref(null);
const tertiarySectionRef = ref(null);

const isHeaderExpanded = ref(true);
const isMiddleVisible = ref(false);
const isTertiaryVisible = ref(false);

const education = [
  {
    institution: 'Multimedia University',
    degree: 'Foundation In Information Technology',
    meta: '3.91 CGPA'
  },
  {
    institution: 'Universiti Kuala Lumpur (MIIT)',
    degree: 'Bachelor of Information Technology (Hons.) in Software Engineering',
    meta: '3.73 CGPA | Dean’s'
  },
  {
    institution: 'LEVEL UP @ SCHOOLS 2019',
    degree: 'Game Development Competition',
    meta: '1st Place - Best Game Title'
  }
];

const projects = [
  {
    title: 'Final Year Project',
    subtitle: 'WelfareCapital - Dynamic Portfolio Management System (DPMS)',
    desc: 'A comprehensive investment portfolio management system. Features include multi-portfolio management and real-time data visualization.',
    image: '/images/wc1.png'
  },
  {
    title: 'Lazer Warzone',
    subtitle: 'MDEC Level Up @ KL Winner',
    desc: 'An award-winning "Auto-Chess" strategy game developed in Unity. Players draft units and position them strategically to defeat opponents in automated battles.',
    image: '/images/lw1.png'
  }
];

const experiences = [
  {
    role: 'Information Technology Intern',
    company: 'Texas Instruments',
    period: 'March 2 – July 3, 2026',
    desc: 'Designed and built a UI for the Material Control System (MCS), replacing a previously manual production-line workflow with a digital, visual interface.',
    highlights: [
      'Built flat-view visualizations of machines across multiple facilities, floors, buildings, and operations to improve production-line visibility',
      'Integrated multiple production APIs into a unified interface, consolidating live machine and process data',
      'Deployed application components using Docker, and worked within a Jira/Confluence/Bitbucket/Artifactory/Jenkins development pipeline'
    ]
  }
];

let observer;

onMounted(() => {
  const options = {
    threshold: [0, 0.5]
  };

  observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.target === mainPageRef.value) {
        if (entry.intersectionRatio <= 0.5) {
          isHeaderExpanded.value = false;
        } else {
          isHeaderExpanded.value = true;
        }
      }

      if (entry.target === middleSectionRef.value) {
        if (entry.isIntersecting) isMiddleVisible.value = true;
      }

      if (entry.target === tertiarySectionRef.value) {
        if (entry.isIntersecting) isTertiaryVisible.value = true;
      }
    });
  }, options);

  if (mainPageRef.value) observer.observe(mainPageRef.value);
  if (middleSectionRef.value) observer.observe(middleSectionRef.value);
  if (tertiarySectionRef.value) observer.observe(tertiarySectionRef.value);
});

onUnmounted(() => {
  if (observer) observer.disconnect();
});
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=DM+Serif+Text:ital@0;1&display=swap');

:root {
  --purple-main: #3C096C;
  --purple-dark: #240046;
  --white: #ffffff;
  --off-white: #f8f8f8;
  --black: #000000;
}

body {
  margin: 0;
  background-color: var(--black);
  font-family: 'DM Serif Text', serif;
}

a {
  color: white;
  text-decoration: none;
}

.shortcut-bar-wrapper {
  position: fixed;
  font-family: monospace;
  height: 3rem;
  display: flex;
  z-index: 100;
  align-items: center;
  color: white;
  width: 100%;
}

.shortcut-bar-wrapper ul {
  display: inline-flex;
  overflow: hidden;
  margin-left: 2rem;
  padding: 0;
}

.shortcut-bar-wrapper li {
  list-style: lower-roman;
  margin: 0 2rem;
  animation: reveal 1.5s cubic-bezier(0.77, 0, 0.175, 1) forwards;
}

.shortcut-bar-wrapper li:hover {
  opacity: 0.5;
}

.shortcut-bar-wrapper label {
  display: inline-flex;
  margin: 0 0 0 1rem;
  font-weight: bold;
}

@keyframes reveal {
  0% {
    transform: translate(0,100%);
  }
  100% {
    transform: translate(0,0);
  }
}

.main-page {
  display: flex;
  width: 100%;
  height: 500px; 
  background: black;
  transition: height 0.5s ease-in-out;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: hidden;
}

.main-page.collapsed {
  height: 200px;
}

.media-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  background-color: black;
  gap: 10px;
  background: url('Images/lagtrain.gif');
  background-position-x: -500px;
  background-size: cover;
  background-position-y: 30%;
}

.top-img-layout {
  overflow: hidden;
  transform: skewY(0deg);
  max-width: 200px;
  height: fit-content;
  position: relative;
  transition: transform 0.6s ease-in-out;
}

.top-img-layout img {
  transform: skewY(-10deg);
  scale: 1.38;
  width: 100%;
}

.top-img-layout.show {
  transform: skewY(10deg);
}

.intro-wrapper {
  display: flex;
  flex-direction: column;
  position: absolute;
  justify-content: center;
  align-items: center;
  color: white;
  width: 100%;
  z-index: 10;
  pointer-events: none;
}

.intro-wrapper h1 {
  font-size: 3rem;
  margin: 0;
}

.intro-wrapper p {
  font-family: inherit;
  margin-top: 0.5rem;
  font-weight: 100;
}

.cinema-section {
  background-color: var(--white);
  color: var(--purple-main);
  min-height: 80vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 4rem 2rem;
  position: relative;
  z-index: 2;
}

.cinema-wrapper {
  display: flex;
  flex-direction: column;
  width: 100%;
  max-width: 1000px;
  gap: 1rem;
}

.cinema-content {
  display: flex;
  width: 100%;
  gap: 3rem;
  align-items: center;
  opacity: 0;
  transform: translateY(30px);
  transition: all 0.8s ease-out;
}

.cinema-section.reveal .cinema-content {
  opacity: 1;
  transform: translateY(0);
}

.cinema-text {
  flex: 1;
}

.cinema-text h2 {
  margin-bottom: 1rem;
  border-bottom: 2px solid var(--purple-main);
  padding-bottom: 5px;
  font-size: larger;
}

.cinema-text p {
  font-size: 1.1rem;
  line-height: 1.6;
  margin-bottom: 2rem;
}

.social {
  margin-top: 1.5rem;
}

.linkedin-btn {
	display: inline-flex;
	align-items: center;
	gap: 8px;
	color: var(--purple-main);
}

.cinema-img-box {
  flex: 1;
  height: 350px;
  box-shadow: 10px 10px 0px var(--purple-main); 
}

.cinema-img-box img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.project-deck {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  opacity: 0;
  transform: translateY(20px);
  transition: all 0.8s ease-out 0.2s;
}

.cinema-section.reveal .project-deck {
  opacity: 1;
  transform: translateY(0);
}

.deck-title {
	margin-bottom: 1rem;
	border-bottom: 2px solid var(--purple-main);
	display: inline-block;
	padding-bottom: 5px;
	font-size: larger;
	font-weight: bold;
}

.p-row {
  display: flex;
  align-items: center;
  gap: 4rem;
  width: 100%;
}

.p-row.reverse {
  flex-direction: row-reverse;
}

.p-visual {
  flex: 1.2;
  position: relative;
  height: 350px;
}

.img-frame {
  width: 100%;
  height: 100%;
  border: 1px solid var(--purple-main);
  background: white;
}

.img-frame img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s;
}

.p-visual:hover .img-frame img {
  transform: scale(1.03);
}

.p-details {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.p-subtitle {
  font-family: monospace;
  font-size: 0.85rem;
  color: #666;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.p-details h3 {
  font-size: 1.8rem;
  color: var(--purple-main);
  margin: 0;
  line-height: 1;
}

.p-details p {
  font-size: 0.95rem;
  line-height: 1.5;
  color: #333;
  margin: 0;
}

.experience-block {
  display: flex;
  flex-direction: column;
  opacity: 0;
  transform: translateY(20px);
  transition: all 0.8s ease-out 0.1s;
}

.cinema-section.reveal .experience-block {
  opacity: 1;
  transform: translateY(0);
}

.exp-timeline {
  display: flex;
  flex-direction: column;
  margin-top: 1rem;
}

.exp-row {
  display: flex;
  gap: 2rem;
}

.exp-marker {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 6px;
}

.exp-dot {
  width: 14px;
  height: 14px;
  border-radius: 50%;
  background: var(--purple-main);
  flex-shrink: 0;
}

.exp-line {
  width: 2px;
  flex: 1;
  background: rgba(60, 9, 108, 0.2);
  margin-top: 4px;
}

.exp-content {
  flex: 1;
  padding-bottom: 1.5rem;
}

.exp-period {
  font-family: monospace;
  font-size: 0.85rem;
  text-transform: uppercase;
  letter-spacing: 1px;
  color: #666;
}

.exp-content h3 {
  font-size: 1.6rem;
  margin: 0.4rem 0 0.1rem 0;
  color: var(--purple-main);
}

.exp-content h4 {
  font-size: 1.05rem;
  font-style: italic;
  font-weight: normal;
  margin: 0 0 1rem 0;
  color: #555;
}

.exp-content p {
  font-size: 0.95rem;
  line-height: 1.5;
  margin: 0 0 1rem 0;
  color: #333;
}

.exp-highlights {
  margin: 0 0 1rem 0;
  padding-left: 1.2rem;
}

.exp-highlights li {
  font-size: 0.9rem;
  line-height: 1.5;
  margin-bottom: 0.5rem;
  color: #333;
}

.list-section {
  background-color: var(--purple-dark);
  color: var(--white);
  padding: 5rem 2rem;
  min-height: 60vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.list-container {
  width: 100%;
  max-width: 900px;
  display: flex;
  flex-direction: column;
}

.list-row {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  border-bottom: 1px solid rgba(255,255,255,0.2);
  padding: 1.5rem 0;
  opacity: 0;
  transform: translateX(-20px);
  transition: all 0.5s ease;
}

.list-section.reveal .list-row {
  opacity: 1;
  transform: translateX(0);
}

.row-left h3 {
  font-size: 1.4rem;
  margin: 0 0 0.3rem 0;
}

.row-left h4 {
  font-size: 1rem;
  color: #ccc;
  margin: 0;
  font-style: italic;
}

.row-right span {
  font-family: monospace;
  font-size: 0.9rem;
  color: #aaa;
}

.link-row {
  border-bottom: none;
  margin-top: 2rem;
  justify-content: flex-start;
}

.link-row a { 
  font-size: 1.2rem; 
  border-bottom: 1px solid white;
  padding-bottom: 5px;
  transition: padding 0.3s;
  display: inline-flex;
  align-items: center;
  gap: 15px;
}

.gh-profile-pic {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  border: 1.5px solid white;
}

.link-row a:hover {
  padding-right: 15px;
}

.about-section {
  font-size: 1rem;
  color: whitesmoke;
  display: flex;
  flex-wrap: wrap;
  background-color: black;
  padding: 2rem;
  img {
    position: relative;
    width: auto;
    height: max(100px, 200px);
    user-select: none;
  }
}

.about-section ul {
  list-style-type: none;
}

.about-section li {
  margin-top: 10px;
  margin-bottom: 10px;
}

.about-section a {
  background-image: linear-gradient(white, white);
  background-size: 0% 0.1rem;
  background-position-y: 100%;
  background-position-x: 0%;
  background-repeat: no-repeat;
  transition: background-size 1s cubic-bezier(0.075, 0.82, 0.165, 1);
  display: inline-flex;
  align-items: center;
  gap: 5px;
}

.about-section a:hover {
  background-size: 100% 0.1rem;
}

.about-section label {
  font-weight: bold;
  text-transform: uppercase;
  font-size: 0.9rem;
  color: gray;
}

.about-section #tag {
  position: relative;
  margin: 2rem;
  width: 100%;
  border-top: 1px solid #333;
  font-weight: bold;
  padding: 0.5rem;
  color: #555;
}

@media screen and (max-width: 768px) {
  .cinema-content {
    flex-direction: column;
  }
  .cinema-img-box {
    width: 100%;
    height: 300px;
  }
  .p-row, .p-row.reverse {
    flex-direction: column;
    gap: 2rem;
  }
  .p-visual {
    width: 100%;
    height: 250px;
  }
  .list-row {
    flex-direction: column;
    gap: 10px;
  }
  .top-img-layout {
    max-width: 100px;
  }
  .exp-row {
    gap: 1rem;
  }
}
</style>