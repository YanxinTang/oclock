<template>
    <div class="base-oclock-dynamic">
        <div class="short" :style="shortStyle"></div>
        <div class="long" :style="longStyle"></div>
    </div>
</template>

<script>
export default {
  name: 'BaseOclockDynamic',
  data() {
    return {
      long: 0,
      short: 0,
      translate: 'translate(0%,-50%)',
      shortDeg: 0,
      date: new Date(),
    };
  },
  computed: {
    longDeg() {
      return `${this.date.getSeconds() * 6}deg`;
    },
    longStyle() {
      return {
        transform: `${this.translate}rotate(${this.longDeg})`,
      };
    },
    shortStyle() {
      return {
        transform: `${this.translate}rotate(${this.shortDeg})`,
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
    .base-oclock-dynamic{
        --radius: 50px;
        width: calc(var(--radius)*2);
        height: calc(var(--radius)*2);
        -webkit-border-radius: var(--radius);
        -moz-border-radius: var(--radius);
        border-radius: var(--radius);
        border: 1px solid #000;
        position: relative;
    }
    .base-oclock-dynamic .short,
    .base-oclock-dynamic .long{
        height: 10px;
        background: #000;
        position: absolute;
        left: 50%;
        top: 50%;
        transform-origin: left center;
        transition: transform .2s linear;
    }
    .base-oclock-dynamic .long{
        width: calc(var(--radius)*0.9);
    }
    .base-oclock-dynamic .short{
        width: calc(var(--radius)*0.7);
    }
</style>

<style scoped>
    .long{

    }
    .short{
        transform: translate(0%,-50%);
    }
</style>
