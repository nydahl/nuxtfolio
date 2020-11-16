<template>
  <div>
    <Nuxt />
  </div>
</template>

<style lang="scss">
:root {
  --bg: #f2f4f9;
  --darkblue: #022d5e;
  --blueshadow: #022d5e5e;
  --peach: #f05d7b;
  --peachshadow: #f05d7a73;
  --green: #acf2d8;
  --greenshadow: #acf2d86e;
  --text: #243951;
  --heading: 'Exo', sans-serif;
}
html {
  font-family:
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  font-size: 10px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
  background-color: var(--bg);
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

h1, h2, h3, h4 {
  font-family: var(--heading);
  color: var(--darkblue);
  text-transform: uppercase;
}
h2 {
  font-size: 4.8rem;
}
h3 {
  font-size: 2.4rem;
}
p {
  color: var(--text);
  font-size: 1.8rem;
}

</style>
