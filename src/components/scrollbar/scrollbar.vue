<!--
 - Author : chenyliu.
 - Date   : 2016/9/3.
 - File   : scrollbar.vue.
 -->
<template>
  <div :class="classes" @click="hello">
    <slot></slot>
  </div>
</template>

<script>
  var Ps = require('./perfect-scrollbar');
  export default {
    props: {
      initParams: {
        type: Object,
        default: function() {
          return {
            handlers: ['click-rail', 'drag-scrollbar', 'keyboard', 'wheel', 'touch'],
            maxScrollbarLength: null,
            minScrollbarLength: null,
            scrollXMarginOffset: 0,
            scrollYMarginOffset: 0,
            stopPropagationOnClick: true,
            suppressScrollX: false,
            suppressScrollY: false,
            swipePropagation: true,
            useBothWheelAxes: false,
            wheelPropagation: false,
            wheelSpeed: 1,
            theme: 'default'
          }
        }
      },
      classes: {
        type: String,
        default: ''
      }
    },
    methods: {
      hello() {
        console.log(this);
      }
    },
    mounted() {
      console.log('test');
      Ps.initialize(this.$el, this.initParams);
    }
  }
</script>

<style lang="less">
  .ps-container {
    -ms-touch-action: none;
    touch-action: none;
    overflow: hidden !important;
    -ms-overflow-style: none;

    > .ps-scrollbar-x-rail {
      display: none;
      position: absolute;
      opacity: 0;
      -webkit-transition: background-color .2s linear, opacity .2s linear;
      -moz-transition: background-color .2s linear, opacity .2s linear;
      -o-transition: background-color .2s linear, opacity .2s linear;
      transition: background-color .2s linear, opacity .2s linear;
      bottom: 0px;
      height: 11px;

      > .ps-scrollbar-x {
        position: absolute;
        background-color: #aaa;
        -webkit-border-radius: 6px;
        -moz-border-radius: 6px;
        border-radius: 6px;
        -webkit-transition: background-color .2s linear, height .2s linear, width .2s ease-in-out, -webkit-border-radius .2s ease-in-out;
        transition: background-color .2s linear, height .2s linear, width .2s ease-in-out, -webkit-border-radius .2s ease-in-out;
        -moz-transition: background-color .2s linear, height .2s linear, width .2s ease-in-out, border-radius .2s ease-in-out, -moz-border-radius .2s ease-in-out;
        -o-transition: background-color .2s linear, height .2s linear, width .2s ease-in-out, border-radius .2s ease-in-out;
        transition: background-color .2s linear, height .2s linear, width .2s ease-in-out, border-radius .2s ease-in-out;
        transition: background-color .2s linear, height .2s linear, width .2s ease-in-out, border-radius .2s ease-in-out, -webkit-border-radius .2s ease-in-out, -moz-border-radius .2s ease-in-out;
        bottom: 2px;
        height: 6px;
      }
      &:hover {
        > .ps-scrollbar-x {
          height: 7px;
        }
      }
      &:active {
        > .ps-scrollbar-x {
          height: 7px;
        }
      }
    }
    > .ps-scrollbar-y-rail {
      display: none;
      position: absolute;
      opacity: 0;
      -webkit-transition: background-color .2s linear, opacity .2s linear;
      -moz-transition: background-color .2s linear, opacity .2s linear;
      -o-transition: background-color .2s linear, opacity .2s linear;
      transition: background-color .2s linear, opacity .2s linear;
      right: 0;
      width: 11px;

      > .ps-scrollbar-y {
        position: absolute;
        background-color: #aaa;
        -webkit-border-radius: 6px;
        -moz-border-radius: 6px;
        border-radius: 6px;
        -webkit-transition: background-color .2s linear, height .2s linear, width .2s ease-in-out, -webkit-border-radius .2s ease-in-out;
        transition: background-color .2s linear, height .2s linear, width .2s ease-in-out, -webkit-border-radius .2s ease-in-out;
        -moz-transition: background-color .2s linear, height .2s linear, width .2s ease-in-out, border-radius .2s ease-in-out, -moz-border-radius .2s ease-in-out;
        -o-transition: background-color .2s linear, height .2s linear, width .2s ease-in-out, border-radius .2s ease-in-out;
        transition: background-color .2s linear, height .2s linear, width .2s ease-in-out, border-radius .2s ease-in-out;
        transition: background-color .2s linear, height .2s linear, width .2s ease-in-out, border-radius .2s ease-in-out, -webkit-border-radius .2s ease-in-out, -moz-border-radius .2s ease-in-out;
        right: 2px;
        width: 6px;
      }
      &:hover {
        > .ps-scrollbar-y {
          width: 7px;
        }
      }
      &:active {
        > .ps-scrollbar-y {
          width: 7px;
        }
      }
    }
    &:hover.ps-in-scrolling {
      pointer-events: none;
    }
    &:hover.ps-in-scrolling.ps-x {
      > .ps-scrollbar-x-rail {
        background-color: #eee;
        opacity: 0.9;

        > .ps-scrollbar-x {
          background-color: #999;
        }
      }
    }
    &:hover.ps-in-scrolling.ps-y {
      > .ps-scrollbar-y-rail {
        background-color: #eee;
        opacity: 0.9;

        > .ps-scrollbar-y {
          background-color: #999;
        }
      }
    }
    &:hover {
      > .ps-scrollbar-x-rail {
        opacity: 0.6;

        &:hover {
          background-color: #eee;
          opacity: 0.9;

          > .ps-scrollbar-x {
            background-color: #999;
          }
        }
      }
      > .ps-scrollbar-y-rail {
        opacity: 0.6;

        &:hover {
          background-color: #eee;
          opacity: 0.9;

          > .ps-scrollbar-y {
            background-color: #999;
          }
        }
      }
    }
  }

  .ps-container.ps-active-x {
    > .ps-scrollbar-x-rail {
      display: block;
      background-color: transparent;
    }
  }

  .ps-container.ps-active-y {
    > .ps-scrollbar-y-rail {
      display: block;
      background-color: transparent;
    }
  }

  .ps-container.ps-in-scrolling {
    pointer-events: none;
  }

  .ps-container.ps-in-scrolling.ps-x {
    > .ps-scrollbar-x-rail {
      background-color: #eee;
      opacity: 0.9;

      > .ps-scrollbar-x {
        background-color: #999;
      }
    }
  }

  .ps-container.ps-in-scrolling.ps-y {
    > .ps-scrollbar-y-rail {
      background-color: #eee;
      opacity: 0.9;

      > .ps-scrollbar-y {
        background-color: #999;
      }
    }
  }

  @supports (-ms-overflow-style:none) {
    .ps-container {
      overflow: auto !important;
    }
  }

  @media screen and (-ms-high-contrast: active), (-ms-high-contrast: none) {
    .ps-container {
      overflow: auto !important;
    }
  }
</style>
