<template>
  <div class="block__container">
    <div class="heading__container">
      <div class="subheading__container">
        <div class="line" />
        <span class="subheading">verktyg</span>
        <div class="line" />
      </div>
      <h2>Det här använder jag</h2>
    </div>
    <div class="toolgrid">
      <div v-for="tool in tools" :key="tool.id" class="tool" :class="tool.order < 7 ? 'tool__left' : 'tool__right'">
        <div class="tool__image">
          <img :src="tool.icon" :alt="tool.title">
        </div>
        <div class="tool__content">
          <h3>{{ tool.title }}</h3>
          <nuxt-content :document="tool" />
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.toolgrid {
  grid-auto-flow: row dense;
  display: grid;
  width: 100%;
  grid-template-columns: 1fr;
  gap: 6rem;
  text-align: left;
}
.tool {
  display: flex;
  flex-direction: column;
  min-height: 17rem;
  align-items: center;
  h3 {
    text-transform: initial;
  }
}

.tool__image {
  img {
    margin-bottom: 1rem;
    display: block;
  }
}
.tool__content {
  text-align: center;
}
.blink {
  animation-name: blink;
  animation-duration: 1s;
  animation-iteration-count: infinite;
}
@keyframes blink {
  0% {
    opacity: 1;
  }
  45% {
    opacity: 1;
  }
  50% {
    opacity: 0.2;
  }
  95% {
    opacity: 0.2;
  }
}

  @media (min-width: 900px) {
  .toolgrid {
    grid-template-columns: 1fr 1fr;
      margin-left: -4rem;

  }
  .tool__left {
    grid-column: 1 / 2;
  }
  .tool__right {
    grid-column: 2 / 3;
  }
  .tool {
    flex-flow: row nowrap;
    align-items: flex-start;
  }
  .tool__image {
    margin-right: 2rem;
    width: 150px;
    flex: 0 0 150px;
    img {
      margin-left: auto;
    }
  }
  .tool__content {
    text-align: left;
  }
}
</style>

<script>
export default {
  name: 'ToolsComponent',
  props: {
    tools: {
      type: Array,
      default () {
        return []
      }
    }
  }
}
</script>
