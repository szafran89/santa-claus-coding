<template>
  <div>
    <div class="colors">
      <div
        v-for="color in colors"
        :key="color.hex"
        class="colors__item"
      >
        <button
          @click="setColor(color.hex)"
          type="button"
          class="colors__item-button"
        >
          <span
            class="colors__item-button-bg"
            :style="{ backgroundColor: color.hex }"
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
  export default {
    data () {
      return {
        colors: [
          {
            label: 'black',
            hex: '#000000',
            codes: ['1D', '1E', '1F', '2C', '2G', '3B', '3H', '4A', '4D', '4I', '5A', '5D', '5I', '6B', '6C', '6J', '7B', '7K']
          },
          {
            label: 'red',
            hex: '#FF0000',
            codes: ['2D', '2E', '3F', '3C', '3D', '3E']
          },
          {
            label: 'yellow',
            hex: '#FFFF00',
            codes: ['9D', '9E', '2F', '3C', '3D', '3F']
          }
        ]
      }
    },
    methods: {
      setColor (hex) {
        this.$emit('setColor', hex)
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
