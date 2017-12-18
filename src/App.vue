<template>
  <div id="app">
    <Colors/>
    <Board/>
  </div>
</template>

<script>
import Colors from './components/Colors'
import Board from './components/Board'

export default {
  name: 'app',
  components: {
    Colors,
    Board
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
