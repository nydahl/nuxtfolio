<template>
  <div class="block__container">
    <div class="heading__container">
      <div class="subheading__container">
        <div class="line" />
        <span class="subheading">projekt</span>
        <div class="line" />
      </div>
      <h2>
        Det här har jag gjort
      </h2>
    </div>
    <div class="projectgrid">
      <div v-for="project in projects" :key="project.id" class="project">
        <div class="project__image">
          <picture>
            <source type="image/webp" :srcset="'projects/' + project.image + '.webp, projects/' + project.image + '@2x.webp 2x'">
            <img :srcset="'projects/' + project.image + '.jpg, projects/' + project.image + '@2x.jpg 2x'" :src="project.image" :alt="project.title">
          </picture>
        </div>
        <div class="project__content">
          <h3><a :href="project.url">{{ project.title }}</a></h3>
          <nuxt-content :document="project" />
          <div class="tags">
            <div v-for="tag in project.tags" :key="tag.id" class="tag">
              {{ tag }}
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="behance__container">
      <h3><a href="https://www.behance.net/nydahl">Jag har mer grejer på Behance, kolla gärna där!</a></h3>
      <a href="https://www.behance.net/nydahl"><img src="behance.svg" alt="behance logo"></a>
    </div>
  </div>
</template>

<style lang="scss">
.projectgrid {
  display: grid;
  width: 100%;
  grid-template-columns: 1fr;
  gap: 6rem;
  text-align: left;
}
.project {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}
.project__content {
  h3 {
    text-transform: initial;
    margin-bottom: 1rem;
    a {
      text-decoration: none;
      color: var(--darkblue);
      display: inline-block;
    }
  }
  p {
    margin-bottom: 2rem;
  }
}
.tags {
  display: block;
  margin-bottom:2rem;
}
.tag {
  text-transform: uppercase;
  font-size: .8rem;
  font-weight: 900;
  opacity: .5;
  display: inline-block;
  padding: .4rem .8rem;
  margin-right: 1rem;
  background-color: var(--darkblue);
  color: white;
  border-radius: 2rem;
  letter-spacing: 1px;
}
.project__image {
  margin-bottom: 2rem;
  picture, img {
    width: 100%;
  }
}
.behance__container {
  border-radius: 0 0 4px 4px;
  text-align: center;
  background-color: var(--peach);
  margin-bottom: -12rem;
  margin-top: 8rem;
  width: calc(100% + 4rem);
  padding: 4rem 6rem;
  h3 {
    a {
      color: white;
      text-decoration: none;
    }
    margin-bottom: 4rem;
  }
  img {
    width: 100%;
    max-width: 40rem;
  }
}
@media (min-width: 767px) {
  .projectgrid {
    grid-template-columns: 1fr 1fr;
  }
  .behance__container {
    width: calc(100% + 12rem);
    padding: 6rem;
  }
  .project__content {
    h3 {
      a {
      &:after {
        content: "BESÖK";
        font-family: var(--heading);
        color: var(--peach);
        opacity: 0;
        transition: all 400ms ease-out;
        font-size: 1.4rem;
        letter-spacing: 0;
        transform: translateX(0);
        display: inline-block;
      }
      &:hover:after {
        letter-spacing: 2px;
        transform: translateX(1rem);
        opacity: 1;
      }
      }
    }
  }
}
</style>

<script>
export default {
  name: 'ProjectsComponent',
  props: {
    projects: {
      type: Array,
      default () {
        return []
      }
    }
  }
}
</script>
