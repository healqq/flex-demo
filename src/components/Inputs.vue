<template>
  <div class="inputs-list">
    <Input 
      v-for="(styleValues, styleKey, index) of styles" 
      :key="index" 
      v-bind:value="currentStyles[styleKey]" 
      v-bind:style-key="styleKey"
      v-bind:values="styleValues"
      v-bind:on-change="onChange">
    </Input>
    <div class="input">
      <label class='input__label'>
        Blocks count
      </label>
      <input type="number" v-model="count" v-on:change="onBlocksCountChange(count)"/>
    </div>
    <div class="input">
      <label class='input__label'>
        <input type="checkbox" v-model="flexToggle" v-on:change="onIsFlexChange(flexToggle)"/>
        Toggle flex
      </label>
      
    </div>
  </div>
</template>

<script>
import Input from './Input';

export default {
  name: 'Inputs',
  props: ['styles', 'onChange', 'currentStyles', 'blocksCount', 'isFlex'],
  components: {
    Input,
  },
  data() {
    return {
      count: this.blocksCount,
      flexToggle: this.isFlex,
    };
  },
  methods: {
    onBlocksCountChange(value) {
      this.$emit('blocks-count-change', value);
    },
    onIsFlexChange(value) {
      this.$emit('is-flex-change', value);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .inputs-list {
    flex: 1;
  }
</style>
