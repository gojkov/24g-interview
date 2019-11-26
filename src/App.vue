<template>
  <div id="app">
    <div class="top-section">
        <Greeting user="Steve" />
        <Header />
    </div>
    <Player />
  </div>
</template>

<script>

import Greeting from './components/Greeting.vue'
import Header from './components/Header.vue'
import Player from './components/Player.vue'

export default {
  name: 'app',
  components: {
    Greeting,
    Header,
    Player
  }
}

</script>

<style lang="scss">

* {
  margin: 0;
  padding: 0;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  font-family: 'Brandon Grotesque Light', sans-serif;
  font-size: 10px;

}

.top-section {
  justify-content: left;
}

</style>
