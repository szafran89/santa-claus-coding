<template>
  <div>
    <div class="colors">
      <div
        v-for="color in colors"
        :key="color.hex"
        class="colors__item"
      >
        <button
          @click="setColor(color)"
          type="button"
          class="colors__item-button"
        >
          <span
            class="colors__item-button-bg"
            :style="{ backgroundColor: '#' + color.hex }"
          ></span>
          {{ color.label }}
        </button>
        <div class="colors__codes">
          <template v-for="code in color.codes">
            {{ code }}
          </template>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import colors from '../../data/colors.json'

  export default {
    data () {
      return {
        colors
      }
    },
    methods: {
      setColor (color) {
        this.$emit('setColor', color)
      }
    }
  }
</script>

<style scoped>
  .colors {
    display: flex;
    flex-direction: row;
  }

  .colors__item {
    width: 100px;
    margin-right: 10px;
    border: 1px solid #444;
  }

  .colors__item-button-bg {
    height: 10px;
    width: 20px;
    display: inline-flex;
  }
</style>
