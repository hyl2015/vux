<template>
  <div class="weui_dialog_alert" v-show="show" @touchmove="!this.scroll && $event.preventDefault()">
    <div v-if="showMask" class="weui_mask" @click="hideOnBlur && (show = false)"></div>
    <div class="weui_dialog" v-show="show" :transition="dialogTransition">
      <slot></slot>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      show: {
        type: Boolean,
        default: false
      },
      showMask: {
        type: Boolean,
        default: true
      },
      maskTransition: {
        type: String,
        default: 'vux-fade'
      },
      dialogTransition: {
        type: String,
        default: 'vux-dialog'
      },
      hideOnBlur: Boolean,
      scroll: {
        type: Boolean,
        default: true
      }
    },
    watch: {
      show (val) {
        this.$emit(val ? 'on-show' : 'on-hide')
      }
    }
  }
</script>

<style lang="less">
  @import '../../styles/weui/widget/weui_tips/weui_mask';
  @import '../../styles/weui/widget/weui_tips/weui_dialog';
</style>
