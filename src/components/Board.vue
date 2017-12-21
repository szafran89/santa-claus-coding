<template>
  <div>
    <div class="board">
      <template v-for="y in board">
        <div class="board__item board__item--label" :key="y.y">
          {{ y.y }}
        </div>
        <div
          v-for="x in y.rows"
          :key="x.code"
          :class="{ 'board__item--label': y.y == 0 }"
          :ref="x.code"
          @click="onSelectCell(x.code)"
          class="board__item"
        >
          {{ x.label ? x.label : '' }}
        </div>
      </template>
    </div>
  </div>
</template>

<script>
  import colors from '../../data/colors.json'
  import board from '../../data/board.json'

  export default {
    props: [
      'selectedColor'
    ],
    data () {
      return {
        colors,
        board
      }
    },
    methods: {
      onSelectCell (code) {
        if (this.selectedColor && this.validateColor(code)) {
          const cell = this.$refs[code][0]
          cell.style.background = '#' + this.selectedColor.hex
        }
      },
      validateColor (code) {
        const codes = this.colors[this.selectedColor.hex].codes
        return codes.includes(code)
      }
    }
  }
</script>

<style scoped>
  .board {
    display: grid;
    grid-template-columns: 50px 50px 50px 50px 50px 50px 50px 50px 50px 50px 50px 50px 50px;
    grid-gap: 1px;
    background-color: #fff;
    color: #444;
  }

  .board .board__item {
    height: 50px;
    border: 1px solid #f1f1f1;
    line-height: 50px;
    color: #000;
    background-color: #fff;
  }

  .board .board__item--label {
    border: none;
  }
</style>
