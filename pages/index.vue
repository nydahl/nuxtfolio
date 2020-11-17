<template>
  <div class="container">
    <section id="intro">
      <h1 class="title">
        Henrik Nydahl
      </h1>
      <span class="lead">Jag sysslar med UX, design och frontend</span>
      <a
        href="mailto:henrik.nydahl@gmail.com"
        class="button button__main"
      >Kontakta mig</a>
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
  }
}
</script>

<style lang="scss">
.container {
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
}
</style>
