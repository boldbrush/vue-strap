<template>
  <span ref="trigger">
    <slot></slot>
    <transition :name="effect">
      <div ref="popover" v-show="show" :class="['tooltip',placement]">
        <div class="tooltip-arrow"></div>
        <div class="tooltip-inner">
          <slot name="content"><div v-html="content"></div></slot>
        </div>
      </div>
    </transition>
  </span>
</template>

<script>
import PopoverMixin from './utils/popoverMixins.js'

export default {
  mixins: [PopoverMixin],
  props: {
    effect: {type: String, default: 'scale'},
    trigger: {type: String, default: 'hover'}
  }
}
</script>

<style>
.tooltip.top,
.tooltip.left,
.tooltip.right,
.tooltip.bottom {
  opacity: .9;
}
.tooltip {
  animation:fadein-in .4s ease-in;
}
.tooltip-inner {
  background-color: #000;
  color: #fff;
  max-width: 200px;
  padding: 15px 18px 14px;
  text-align: center;
  font-size: 13px;
  -webkit-border-radius: 4px;
}
.fadein-enter {
  animation:fadein-in 0.4s ease-in;
}
.fadein-leave-active {
  animation:fadein-out 0.6s ease-out;
}
@keyframes fadein-in {
  0% {
    opacity: 0;
  }
  100% {
    opacity: .9;
  }
}
@keyframes fadein-out {
  0% {
    opacity: .9;
  }
  100% {
    opacity: 0;
  }
}
</style>
