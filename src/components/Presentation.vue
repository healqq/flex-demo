<template>
  <div class="presentation" 
    v-bind:style="currentStyles" 
    v-bind:class="containerClasses">
    <div class="presentation__block" v-for="(block, index) in blocks" :key="index"
      v-bind:class="`presentation__block--${index}`">
      {{index}}
    </div>
  </div>
</template>

<script>
export default {
  name: 'Presentation',
  props: ['currentStyles', 'blocksCount', 'isFlex'],
  data() {
    return {
      blocks: new Array(this.blocksCount).fill(0),
    };
  },
  watch: {
    blocksCount() {
      this.blocks = new Array(this.blocksCount).fill(0);
    },
  },
  computed: {
    containerClasses() {
      return [`presentation--${this.currentStyles['flex-direction']}`, this.isFlex ? 'presentation--with-flex' : ''];
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .presentation {
    display: flex;
    flex: 2;
    height: 100vh;
    border: 2px dashed #aaa;
    box-sizing: border-box;
  }
  .presentation__block {
    margin: 10px;
    border: 2px solid orange;
    font-size: 22pt;
    text-align: center;
    color: black;
    transform: flex 0.3s ease-out;
  }
  .presentation--with-flex {
    .presentation__block {
    }
    @for $i from 1 through 50 {
      .presentation__block--#{$i} {
        flex: $i;
      }
    }
  }

  .presentation--row {
    .presentation__block {
      width: 40px;
    }
    @for $i from 1 through 50 {
      .presentation__block--#{$i} {
        height: 40px + $i * 10px;
        line-height: 40px + $i * 10px;
      }
    }
  }

  .presentation--column {
    .presentation__block {
      height: 40px;
    }
    @for $i from 1 through 50 {
      .presentation__block--#{$i} {
        width: 40px + $i * 10px;
      }
    }
  }
</style>
