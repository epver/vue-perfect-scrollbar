<template>
  <div id="app">
    <scrollbar :classes="'contentHolder'">
      <div class="content">
        <div class="kolom"></div>
        <div class="kolom"></div>
        <div class="kolom"></div>
        <div class="kolom"></div>
        <div class="kolom"></div>
        <div class="kolom"></div>
        <div class="kolom"></div>
        <div class="kolom"></div>
        <div class="kolom"></div>
        <div class="kolom"></div>
        <div class="kolom"></div>
        <div class="kolom"></div>
        <div class="clear"></div>
      </div>
    </scrollbar>
    <div class="spacer">
      <h1>default</h1>
    </div>
  </div>
</template>

<script>
import Scrollbar from './components/scrollbar'
export default {
  data () {
    return {
    }
  },
  components: {
    Scrollbar
  }
}
</script>

<style lang="less">
  .contentHolder {
    position: relative;
    margin: 0px auto;
    padding: 0px;
    width: 400px;
    height: 400px;
    overflow: auto;
  }
  .content {
    background: #EEE;
    min-width: 750px;
  }

  .kolom {
    background: #2196F3;
    width: 150px;
    height: 150px;
    float: left;
    display: inline-block;
    margin: 15px;
  }
  .clear{
    clear: both;
  }
  .spacer {
    text-align: center
  }
</style>
