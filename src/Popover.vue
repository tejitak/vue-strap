<template>
<span>
  <span ref="trigger">
    <slot></slot>
  </span>
  <div ref="popover"
    :class="['popover',placement]"
    :transition="effect"
  >
    <div class="arrow"></div>
    <h3 class="popover-title" v-if="title">
      <div name="title">{{title}}</div>
    </h3>
    <div class="popover-content">
      <div name="content" v-html="content"></div>
    </div>
  </div>
</span>
</template>

<script>
import PopoverMixin from './popoverMixins.js'

export default {
  mixins: [PopoverMixin],
  props: {
    trigger: {
      type: String,
      default: 'click'
    }
  }
}
</script>

<style>
.scale-transition, .scale-enter-active, .scale-leave-active,
.fade-transition, .fade-enter-active, .fade-leave-active {
  display: block;
}
.scale-enter {
  animation:scale-in 0.15s ease-in;
}
.scale-leave, .scale-leave-active {
  animation:scale-out 0.15s ease-out;
}
@keyframes scale-in {
  0% {
    transform: scale(0);
    opacity: 0;
  }
  100% {
    transform: scale(1);
    opacity: 1;
  }
}
@keyframes scale-out {
  0% {
    transform: scale(1);
    opacity: 1;
  }
  100% {
    transform: scale(0);
    opacity: 0;
  }
}
</style>
