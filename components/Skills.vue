<template>
  <div class="portrait__container">
    <img ref="portrait" src="/jag.png" alt="Porträtt" class="portrait">
    <div class="block__container">
      <div class="heading__container">
        <div class="subheading__container">
          <div class="line" />
          <span class="subheading">skills</span>
          <div class="line" />
        </div>
        <h2>
          Det här kan jag
        </h2>
      </div>
      <div class="skillgrid">
        <div v-for="skill in skills" :key="skill.id" class="skill">
          <div class="skill__image">
            <img :src="skill.icon" :alt="skill.title">
          </div>
          <div class="skill__content">
            <h3>{{ skill.title }}</h3>
            <nuxt-content :document="skill" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.portrait__container {
  position: relative;
  margin-top: 14rem;
  .portrait {
    margin: 0 auto;
    max-width: 410px;
    left: 0;
    right: 0;
    width: 100%;
    top: -22%;
    z-index: -10;
    position: absolute;
  }
}
.block__container {
  background-color: white;
  border-radius: 4px;
  box-shadow: 0 44px 99px var(--blueshadow);
  width: 100%;
  text-align: center;
  padding: 6rem 2rem 6rem 2rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 14rem;
}
.heading__container {
  display: flex;
  flex-flow: row nowrap;
  flex-direction: column;
  margin-bottom: 6rem;
}
.subheading__container {
  padding: 0 2rem;
  width: 100%;
  display: flex;
  flex-flow: row nowrap;
  align-items: center;
  justify-content: center;
  opacity: .5;
  margin-bottom: 2rem;
  .line {
    flex: 1 1 auto;
    display: block;
    height: 2px;
    background-color: var(--darkblue);
    &:last-child {
      margin-left: 2rem;
    }
    &:first-child {
      margin-right: 2rem;
    }
  }
}
.subheading {
  flex: 0 1 auto;
  font-family: var(--heading);
  color: var(--darkblue);
  text-transform: uppercase;
  letter-spacing: 12px;
  font-size: 1.8rem;
  display: block;
}

.skillgrid {
  display: grid;
  width: 100%;
  grid-template-columns: 1fr;
  gap: 6rem;
  text-align: left;
}
.skill {
  display: flex;
  flex-flow: column;
  align-items: center;
}
.skill__image {
  filter: drop-shadow(0 10px 10px var(--greenshadow));
  margin-right: 0;
  margin-bottom: 3rem;
}
.skill__content {
  text-align: center;
}

@media (min-width: 767px) {
  .block__container {
    padding: 6rem 6rem 12rem 6rem;
    margin-bottom: 22rem;
  }
  .portrait__container {
    margin-top: 0;
    position: relative;
    &:hover .portrait {
      transform: translate3d(30px, -138px, 0px) rotate3d(0, 0, 1, 11deg);
    }
    .portrait {
      width: unset;
      left: unset;
      position: absolute;
      top: -277px;
      right: 70px;
      z-index: -10;
      transition: transform 400ms cubic-bezier(0.72, -0.6, 0.37, 1.58);
    }
  }
  .skillgrid {
    display: grid;
    width: 100%;
    grid-template-columns: 1fr 1fr;
    gap: 6rem;
    text-align: left;
  }
  .skill {
    flex-flow: row nowrap;
    align-items: flex-start;
  }
  .skill__image {
    margin-right: 2rem;
    margin-bottom: 0;
  }
  .skill__content {
    text-align: left;
  }
  .heading__container {
    margin-bottom: 8rem;
  }
  .subheading {
    font-size: 2.4rem;
  }
  .subheading__container {
  margin-bottom: 3rem;
  padding: 0;
  }
}
</style>

<script>
export default {
  name: 'SkillsComponent',
  props: {
    skills: {
      type: Array,
      default () {
        return []
      }
    }
  }
}
</script>
