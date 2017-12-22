<template>
  <div class="summary">
    <div class="summary__item">
      Checked: {{summary.checked}}/{{ codesSum }}
    </div>
    <div class="summary__item">
      Points: {{summary.points}}/{{ codesSum }}
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
  .summary .summary__item {
    width: 100%;
    padding: 5px;
    font-weight: bold;
    text-align: left;
  }
</style>
