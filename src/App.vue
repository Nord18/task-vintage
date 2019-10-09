<template>
  <div id="app">
    <Contacts />
    <Offices />
    <Registration />
  </div>
</template>

<script>
import Contacts from './views/Contacts.vue'
import Offices from './views/Offices.vue'
import Registration from './views/Registration.vue'

export default {
  name: 'app',
  components: {
    Contacts,
    Offices,
    Registration
  }
}
</script>

<style lang="scss">
@import '~bootstrap/dist/css/bootstrap-grid.min.css';

@font-face {
  font-family: "Suisse Int'l";
  src: url('./assets/fonts/SuisseIntl.woff') format('woff');
  font-weight: 400;
}

@font-face {
  font-family: "Suisse Int'l";
  src: url('./assets/fonts/SuisseIntl-Light.woff') format('woff');
  font-weight: 300;
}

@font-face {
  font-family: "Suisse Int'l";
  src: url('./assets/fonts/SuisseIntl-SemiBold.woff') format('woff');
  font-weight: 600;
}

body {
  font-family: "Suisse Int'l";
}

body,h1,h2,h3,p,a,button,li,ul,span {
  margin: 0;
  padding: 0;
}

ul {
  list-style: none;
}

a {
  text-decoration: none;
}
</style>
