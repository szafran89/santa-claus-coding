<template>
  <div id="app" class="container">
    <main class="template">
      <div class="template__board">
        <Board
          :selected-color="selectedColor"
          :colors="colors"
          :board="board"
          v-on:setSummary="setSummary"
        />
      </div>
      <div class="template__sidebar">
        <Colors
          :colors="colors"
          v-on:setColor="setColor"
          v-if="summary.checked !== codesSum"
        />
        <Summary :codesSum="codesSum" :summary="summary" />
      </div>
    </main>
  </div>
</template>

<script>
  import Colors from './components/Colors'
  import Board from './components/Board'
  import Summary from './components/Summary'
  import colors from '../data/colors.json'
  import board from '../data/board.json'

  export default {
    name: 'app',
    components: {
      Colors,
      Board,
      Summary
    },
    data () {
      return {
        colors,
        board,
        selectedColor: null,
        summary: {
          checked: 0,
          points: 0
        }
      }
    },
    computed: {
      codesSum () {
        return Object.keys(this.colors)
          .map((key, index) => this.colors[key].codes.length)
          .reduce((a, b) => a + b, 0)
      }
    },
    methods: {
      setColor (color) {
        this.selectedColor = color
      },
      setSummary (checked, points) {
        this.summary = {
          checked,
          points
        }
      }
    }
  }
</script>

<style>
  body {
    margin-top: 20px;
  }

  .container {
    max-width: 1024px;
    margin: 0 auto;
    text-align: center;
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
  }

  .template {
    display: flex;
  }

  .template__board {
    padding: 10px;
    border: 1px solid #f1f1f1;
  }

  .template__sidebar {
    margin-left: 20px;
    padding: 10px;
    border: 1px solid #f1f1f1;
  }
</style>
