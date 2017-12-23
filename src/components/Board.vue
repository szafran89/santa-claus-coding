<template>
  <div class="board">
    <template v-for="y in board">
      <div class="board__item board__item--label" :key="y.y">
        {{ y.y === 0 ? '' : y.y }}
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
</template>

<script>
  export default {
    props: [
      'colors',
      'board',
      'selectedColor'
    ],
    data () {
      return {
        checkedCodesSum: 0,
        points: 0
      }
    },
    methods: {
      onSelectCell (code) {
        if (this.selectedColor && this.validateColor(code)) {
          const cell = this.$refs[code][0]
          if (cell.style.background === '') {
            cell.style.background = '#' + this.selectedColor.hex
            cell.classList.add('board__item--checked')
            this.$emit('setSummary', ++this.checkedCodesSum, ++this.points)
          } else {
            cell.style.background = ''
            cell.classList.remove('board__item--checked')
            this.$emit('setSummary', --this.checkedCodesSum, --this.points)
          }
        } else {
          if (this.selectedColor) {
            this.$emit('setSummary', this.checkedCodesSum, --this.points)
          } else {
            alert('You have to select color!')
          }
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
    display: -ms-grid;
    display: grid;
    -ms-grid-columns: 35px 35px 35px 35px 35px 35px 35px 35px 35px 35px 35px 35px 35px;
    grid-template-columns: 35px 35px 35px 35px 35px 35px 35px 35px 35px 35px 35px 35px 35px;
    grid-gap: 1px;
    padding: 5px;
    background-color: #fff;
    color: #444;
  }

  .board__item {
    height: 35px;
    border: 1px solid #d4d4d4;
    line-height: 35px;
    cursor: pointer;
    color: #000;
    background-color: #fff;
  }

  .board__item:hover {
    background-color: #f1f1f1;
  }

  .board__item--label {
    border: none;
  }
</style>
