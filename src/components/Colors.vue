<template>
  <div class="colors">
    <div
      v-for="color in colors"
      :key="color.hex"
      class="colors__item"
    >
      <button
        @click="setColor(color, $event)"
        type="button"
        class="colors__item-button"
      >
        <span
          class="colors__item-button-bg"
          :style="{ backgroundColor: '#' + color.hex }"
        ></span>
        {{ color.label }}
        <span
          class="colors__item-button-icon"
        ></span>
      </button>
      <div class="colors__codes">
        <span
          v-for="code in color.codes"
          :key="code.hex"
          class="colors__item-hex"
        >
          {{ code }},
        </span>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    props: [
      'colors'
    ],
    methods: {
      setColor (color, event) {
        const activeColor = this.$el.querySelector('.colors_item-button--active')
        if (activeColor) {
          activeColor.classList.remove('colors_item-button--active')
        }
        event.target.classList.toggle('colors_item-button--active')
        this.$emit('setColor', color)
      }
    }
  }
</script>

<style scoped>
  .colors {
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
    padding-bottom: 20px;
    border-bottom: 1px solid #f1f1f1;
  }

  .colors__item {
    width: 100%;
    margin-bottom: 20px;
  }

  .colors__item {
    text-align: left;
  }

  .colors__item-button {
    display: flex;
    align-items: center;
    justify-content: flex-start;
    width: 100%;
    margin-bottom: 10px;
    padding: 10px 0;
    border: none;
    font-size: 14px;
    text-transform: uppercase;
    text-align: left;
    cursor: pointer;
  }

  .colors_item-button--active .colors__item-button-icon {
    display: none;
    display: inline-flex;
    width: 20px;
    height: 20px;
    margin-left: 10px;
    background-size: 20px;
    background-repeat: no-repeat;
    background-image: url(data:image/svg+xml;utf8;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iaXNvLTg4NTktMSI/Pgo8IS0tIEdlbmVyYXRvcjogQWRvYmUgSWxsdXN0cmF0b3IgMTkuMC4wLCBTVkcgRXhwb3J0IFBsdWctSW4gLiBTVkcgVmVyc2lvbjogNi4wMCBCdWlsZCAwKSAgLS0+CjxzdmcgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayIgdmVyc2lvbj0iMS4xIiBpZD0iTGF5ZXJfMSIgeD0iMHB4IiB5PSIwcHgiIHZpZXdCb3g9IjAgMCA0MjYuNjY3IDQyNi42NjciIHN0eWxlPSJlbmFibGUtYmFja2dyb3VuZDpuZXcgMCAwIDQyNi42NjcgNDI2LjY2NzsiIHhtbDpzcGFjZT0icHJlc2VydmUiIHdpZHRoPSI1MTJweCIgaGVpZ2h0PSI1MTJweCI+CjxwYXRoIHN0eWxlPSJmaWxsOiM2QUMyNTk7IiBkPSJNMjEzLjMzMywwQzk1LjUxOCwwLDAsOTUuNTE0LDAsMjEzLjMzM3M5NS41MTgsMjEzLjMzMywyMTMuMzMzLDIxMy4zMzMgIGMxMTcuODI4LDAsMjEzLjMzMy05NS41MTQsMjEzLjMzMy0yMTMuMzMzUzMzMS4xNTcsMCwyMTMuMzMzLDB6IE0xNzQuMTk5LDMyMi45MThsLTkzLjkzNS05My45MzFsMzEuMzA5LTMxLjMwOWw2Mi42MjYsNjIuNjIyICBsMTQwLjg5NC0xNDAuODk4bDMxLjMwOSwzMS4zMDlMMTc0LjE5OSwzMjIuOTE4eiIvPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8L3N2Zz4K);
  }

  .colors__item-button-bg {
    height: 20px;
    width: 20px;
    display: inline-flex;
    margin-right: 10px;
    border: 1px solid #f1f1f1;
  }
</style>
