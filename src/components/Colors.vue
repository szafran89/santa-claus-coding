<template>
  <div>
    <div class="colors">
      <div v-for="color in colors" :key="color.hex" class="colors__item colors__item--black">
        {{ color.label }}
        <div class="colors__codes">
          1D, 1E, 1F
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
            label: 'Black',
            hex: '#000',
            codes: ['1D', '1E', '1F', '2C', '2G', '3B', '3H', '4A', '4D', '4I', '5A', '5D', '5I', '6B', '6C', '6J', '7B', '7K']
          },
          {
            label: 'Red',
            hex: '#FF0000',
            codes: ['2D', '2E', '3F', '3C', '3D', '3E']
          },
          {
            label: 'Yellow',
            hex: '#FFFF00',
            codes: ['9D', '9E', '2F', '3C', '3D', '3F']
          }
        ]
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

  .colors__item--black {
    background-color: black;
  }

  .colors__item--red {
    background-color: red;
  }

  .colors__item--yellow {
    background-color: yellow;
  }
</style>
