<template>
  <div id="app">
    {{ selectedColor ? 'Selected color: ' + selectedColor.label : 'You have to select color' }}
    <Colors v-on:setColor="setColor" />
    <Board :selected-color="selectedColor"/>
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
  },
  data () {
    return {
      selectedColor: null
    }
  },
  methods: {
    setColor (color) {
      this.selectedColor = color
    }
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
