<template>
    <div class="box" v-clipboard:copy="css" @click="isCopied">
        <div :class="className">
            <slot></slot>
            <slot name="innerHtml"></slot>
        </div>
    </div>
</template>

<script>
export default {
  name: 'Box.vue',

  data() {
    return {
      css: this.rawCss,
    };
  },

  props: {
    rawCss: {
      type: String,
      default: '',
    },
    className: {
      type: String,
      default: '',
    },
  },

  methods: {
    isCopied() {
      this.$store.dispatch('messageHandler');
    },
  },
};
</script>

<style lang="scss" scoped>

    .box {
        min-height: 60px;
        min-width: 30px;
        cursor: pointer;
        display: flex;
        align-items: center;
    }
</style>
