<template>
    <div class="base-oclock">
        <div class="short" :style="shortStyle"></div>
        <div class="long" :style="longStyle"></div>
    </div>
</template>

<script>
export default {
  name: 'BaseOclock',
  data() {
    return {
      long: 0,
      short: 0,
      translate: 'translate(0%,-50%)',
      date: new Date(),
    };
  },
  props: {
    shortDeg: Number,
    longDeg: Number,
  },
  computed: {
    longStyle() {
      return {
        transform: `${this.translate} rotate(${this.longDeg}deg)`,
      };
    },
    shortStyle() {
      return {
        transform: `${this.translate} rotate(${this.shortDeg}deg)`,
      };
    },
  },
  mounted() {
    this.timer = setInterval(() => {
      this.date = new Date();
    }, 1000);
  },
};
</script>

<style>
    .base-oclock{
        --radius: 50px;
        width: calc(var(--radius)*2);
        height: calc(var(--radius)*2);
        -webkit-border-radius: var(--radius);
        -moz-border-radius: var(--radius);
        border-radius: var(--radius);
        position: relative;
    }
    .base-oclock .short,
    .base-oclock .long{
        height: 10px;
        background: #000;
        position: absolute;
        left: 50%;
        top: 50%;
        transform-origin: left center;
        transition: transform .2s linear;
    }
    .base-oclock .long{
        width: calc(var(--radius)*0.9);
    }
    .base-oclock .short{
        width: calc(var(--radius)*0.7);
    }
</style>

<style scoped>

</style>

