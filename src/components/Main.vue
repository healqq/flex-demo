<template>
  <div class="container">
    <Inputs v-bind:on-change="setStyle" v-bind:styles="styles" 
    v-bind:blocks-count="blocksCount"
    v-bind:is-flex="isFlex"
    v-on:is-flex-change="setIsFlex"
    v-on:blocks-count-change="setBlocksCount" 
    v-bind:current-styles="currentStyles"></Inputs>
    <Presentation 
      v-bind:current-styles="currentStyles"
       v-bind:is-flex="isFlex"
      v-bind:blocks-count="blocksCount">
    </Presentation>
  </div>
</template>

<script>
import Presentation from './Presentation';
import Inputs from './Inputs';

export default {
  name: 'Main',
  components: {
    Presentation,
    Inputs,
  },
  data() {
    return {
      isFlex: false,
      blocksCount: 8,
      styles: {
        'flex-direction': ['row', 'column'],
        'flex-wrap': ['nowrap', 'wrap', 'wrap-reverse'],
        'justify-content': ['flex-start', 'flex-end', 'center', 'space-between', 'space-around', 'space-evenly'],
        'align-items': ['flex-start', 'flex-end', 'center', 'stretch', 'baseline'],
        'align-content': ['flex-start', 'flex-end', 'center', 'stretch', 'space-between', 'space-around'],
      },
      currentStyles: {
        'flex-direction': 'row',
        'flex-wrap': 'nowrap',
        'justify-content': 'flex-start',
        'align-items': 'flex-start',
        'align-content': 'stretch',
      },
    };
  },
  methods: {
    setIsFlex(value) {
      this.isFlex = value;
    },
    setStyle(key, value) {
      this.currentStyles[key] = value;
    },
    setBlocksCount(value) {
      this.blocksCount = parseInt(value, 10);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
</style>
