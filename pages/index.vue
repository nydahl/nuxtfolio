<template>
  <div class="container">
    <div id="themeswitch" :class="{ active: light }" @click="toggleTheme">
      <svg id="regular" xmlns="http://www.w3.org/2000/svg" width="36" height="36" viewBox="0 0 36 36">
        <path id="line" d="M21.38,31.5H14.63a1.13,1.13,0,1,1,0-2.25h6.75a1.13,1.13,0,0,1,0,2.25Z" />
        <path id="top" d="M18,5.19a1.13,1.13,0,0,1-1.12-1.13V1.13a1.13,1.13,0,1,1,2.25,0V4.06A1.14,1.14,0,0,1,18,5.19Z" />
        <path id="top_right" d="M27.86,9.27a1.13,1.13,0,0,1-.8-1.92l2.08-2.08a1.12,1.12,0,1,1,1.59,1.59L28.65,8.94A1.12,1.12,0,0,1,27.86,9.27Z" />
        <path id="right" d="M34.88,19.13H31.94a1.13,1.13,0,1,1,0-2.25h2.94a1.13,1.13,0,0,1,0,2.25Z" />
        <path id="bottom_right" d="M29.93,31.06a1.11,1.11,0,0,1-.79-.33l-2.08-2.08a1.12,1.12,0,1,1,1.59-1.59l2.08,2.08a1.13,1.13,0,0,1-.8,1.92Z" />
        <path id="bottom_left" d="M6.07,31.06a1.13,1.13,0,0,1-.8-1.92l2.08-2.08a1.12,1.12,0,1,1,1.59,1.59L6.86,30.73A1.11,1.11,0,0,1,6.07,31.06Z" />
        <path id="left" d="M4.06,19.13H1.13a1.13,1.13,0,1,1,0-2.25H4.06a1.13,1.13,0,1,1,0,2.25Z" />
        <path id="top_left" d="M8.14,9.27a1.12,1.12,0,0,1-.79-.33L5.27,6.86A1.12,1.12,0,1,1,6.86,5.27L8.94,7.35a1.13,1.13,0,0,1-.8,1.92Z" />
        <path id="yellow" d="M28.5,18a10.49,10.49,0,0,1-4,8.25,5,5,0,0,0-1.92,3,.12.12,0,0,0-.08,0h-9a.18.18,0,0,0-.1,0,4.57,4.57,0,0,0-1.71-2.88A10.5,10.5,0,1,1,28.5,18Z" fill="#ffc107" />
        <path id="glare" d="M23.63,18.75a1.12,1.12,0,0,1-1.13-1.12,4.13,4.13,0,0,0-4.12-4.13,1.13,1.13,0,1,1,0-2.25,6.38,6.38,0,0,1,6.37,6.38A1.12,1.12,0,0,1,23.63,18.75Z" />
        <path id="bulb" d="M19.88,36H16.13c-1.27,0-2.63-1-2.63-3.07V30.29a4.89,4.89,0,0,0-1.81-3.91,10.49,10.49,0,1,1,12.8-.13,4.85,4.85,0,0,0-2,3.79v3.34A2.63,2.63,0,0,1,19.88,36ZM18,9.75A8.24,8.24,0,0,0,13,24.58a7.14,7.14,0,0,1,2.71,5.71v2.64c0,.14,0,.82.37.82h3.75a.38.38,0,0,0,.38-.37V30a7.11,7.11,0,0,1,2.85-5.56A8.25,8.25,0,0,0,18,9.75Z" />
      </svg>
    </div>
    <section id="intro">
      <h1 class="title">
        Henrik Nydahl
      </h1>
      <span class="lead">Jag sysslar med UX, design och frontend</span>
      <a
        href="mailto:henrik.nydahl@gmail.com"
        class="button button__main"
      >
        Kontakta mig
      </a>
    </section>
    <Skills :skills="skills" />
    <Tools :tools="tools" />
    <Projects :projects="projects" />
  </div>
</template>

<script>
export default {
  async asyncData ({ $content }) {
    const skills = await $content('skills').fetch()
    const tools = await $content('tools').sortBy('order').fetch()
    const projects = await $content('projects').fetch()
    return {
      skills,
      tools,
      projects
    }
  },
  data () {
    return {
      light: true
    }
  },
  methods: {
    toggleTheme () {
      this.light = !this.light
      document.documentElement.classList.toggle('dark')
    }
  }
}
</script>

<style lang="scss">
#themeswitch {
  cursor: pointer;
  width: 36px;
  height: 36px;
  position: fixed;
  top: 1rem;
  right: 1rem;
  z-index: 100;
  user-select: none;
  &:focus {
    outline: none;
  }
  svg {
    #top, #top_left, #left, #bottom_left, #bottom_right, #right, #top_right {
      transition: transform 300ms ease-in-out, opacity 300ms ease-in-out;
      opacity: 0;
    }
    transition: fill 300ms ease-in-out;
    fill: var(--darkblue);
    #top {transform: translate3d(0,9px,0);}
    #top_left {transform: translate3d(9px,9px,0);}
    #left {transform: translate3d(9px,0,0);}
    #bottom_left {transform: translate3d(9px,-9px,0);}
    #bottom_right {transform: translate3d(-9px,-9px,0);}
    #right {transform: translate3d(-9px,0,0);}
    #top_right {transform: translate3d(-9px,9px,0);}
    #yellow {
      transition: opacity 300ms ease-in-out;
      fill: #ffd258;
      opacity: 0;
    }
  }
  &.active {
    svg {
      #top, #top_left, #left, #bottom_left, #bottom_right, #right, #top_right {
        transform: translate3d(0,0,0);
        opacity: 1;
      }
      #yellow {
        opacity: 1;
      }
    }
  }
}
.container {
  position: relative;
  max-width: 1200px;
  margin: 0 auto;
  flex-direction: column;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  padding: 2rem;
}

#intro {
  min-height: 65vh;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  text-align: center;
}

.title {
  display: block;
  font-size: 64px;
  color: var(--darkblue);
  letter-spacing: 1px;
  text-transform: unset;
}

.lead {
  font-size: 32px;
  color: var(--peach);
  padding-bottom: 15px;
  display: block;
  font-family: var(--heading);
  margin-bottom: 4rem;
  transition: text-shadow 300ms ease-in-out;
  text-shadow: 2px 2px 0px var(--bg);
}

.button {
  display: inline-block;
  font-family: var(--heading);
  color: white;
  background-color: var(--peach);
  text-transform: uppercase;
  letter-spacing: 2px;
  text-decoration: none;
  padding: 2rem 3rem;
  font-size: 2rem;
  border-radius: 6rem;
  box-shadow: 0 13px 24px var(--peachshadow);
  transition: all 300ms ease-in-out;
  transform: translate3d(0, 0, 0);
  will-change: transform;
  &:hover {
    transform: translate3d(0, 4px, 0);
    box-shadow: 0 9px 16px var(--peachshadow);
  }
}
@media (min-width: 767px) {
  #intro {
    min-height: 75vh;
    align-items: flex-start;
  }
  #themeswitch {
    position: absolute;
    top: 2rem;
    right: 0;
    &:hover svg #yellow {
      opacity: .5;
    }
  }
}
</style>
