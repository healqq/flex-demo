<template>
  <div class="input">
    <header class="input__header">
      {{styleKey}}
    </header>
    <label class="input__label"
      v-for="(val, index) in values" 
      :key="index">
      <input type="radio"   
        v-bind:value="val"
        v-model="value"
        v-on:change="onChange(styleKey, value)">
      {{val}}
    </label>
  </div>
</template>

<script>
export default {
  props: ['value', 'styleKey', 'onChange', 'values'],
  name: 'Input',
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
  .input__header {
    font-weight: bold;
    line-height: 1.4;
  }
  .input {
    text-align: left;
    padding: 10px;
  }
  .input__label {
    display: block;
    text-align: left;
  }
</style>
