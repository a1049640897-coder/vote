<template>
  <div class="wrapper" ref="wrapper">
    <div class="content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
  import BScroll from "better-scroll";

  export default {
    name: "Scroll",
    props: {
      probeType: {
        type: Number,
        default: 0,
      },

    },
    data() {
      return {
        scroll: {}
      }
    },
    methods: {
      refresh() {
        this.scroll && this.scroll.refresh();
      },
    },
    mounted() {
      this.scroll = new BScroll(this.$refs.wrapper, {
        click: true,
        probeType: this.probeType,
      });
      if (this.probeType == 2 || this.probeType == 3) {
        this.scroll.on("scroll", (position) => {
          this.$emit('scroll', position)
        });
      }
    }
  }
</script>

<style scoped>

</style>