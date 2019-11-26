<template>
  <div id="app">
    <b-container fluid>

      <b-row>
        <b-col cols="12">
          <Greeting user="Steve" />
          <Header />
        </b-col>
      </b-row>
      
      <b-row>
        <b-col cols="12">
          <Player />
        </b-col>
      </b-row>
     
    </b-container>
    
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
  font-family: 'Brandon Grotesque Medium', sans-serif;
  font-size: 10px;

}

</style>
