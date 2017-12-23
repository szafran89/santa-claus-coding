<template>
  <div class="summary">
    <div class="summary__item">
      Checked: {{summary.checked}}/{{ codesSum }}
    </div>
    <div class="summary__item">
      Points: {{summary.points}}/{{ codesSum }}
    </div>
    <div class="summary__success" v-if="summary.checked === codesSum">
      <div class="summary__success-text">
        Looks like you nailed it, kid! 👏 🎉 🎊 🎄
      </div>
      <img src="https://media2.giphy.com/media/3o6fJ93v9wb1FqEtPO/giphy.gif">
    </div>
  </div>
</template>

<script>
  export default {
    props: [
      'codesSum',
      'summary'
    ]
  }
</script>

<style scoped>
  .summary__item {
    width: 100%;
    padding: 5px;
    font-weight: bold;
    text-align: left;
  }

  .summary__success-text {
    margin: 10px 0;
    font-weight: bold;
  }
</style>
