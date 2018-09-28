<template>
  <div id="app">
    <DigitalSingle :value="hHour"></DigitalSingle>
    <DigitalSingle :value="lHour"></DigitalSingle>
    <DigitalSingle :value="hMiniute"></DigitalSingle>
    <DigitalSingle :value="lMiniute"></DigitalSingle>
    <DigitalSingle :value="hSeconds"></DigitalSingle>
    <DigitalSingle :value="lSeconds"></DigitalSingle>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import DigitalSingle from './components/DigitalSingle.vue';

export default {
  name: 'app',
  components: {
    HelloWorld,
    DigitalSingle,
  },
  data(){
    return {
      date: new Date(),
    };
  },
  computed: {
    hHour(){
      const hour = this.date.getHours();
      return parseInt(hour / 10);
    },
    lHour(){
      const hour = this.date.getHours();
      return parseInt(hour % 10);
    },
    hMiniute(){
      const miniute = this.date.getMinutes();
      return parseInt(miniute / 10);
    },
    lMiniute(){
      const miniute = this.date.getMinutes();
      return parseInt(miniute % 10);
    },
    hSeconds(){
      const Seconds = this.date.getSeconds();
      return parseInt(Seconds / 10);
    },
    lSeconds(){
      const Seconds = this.date.getSeconds();
      return parseInt(Seconds % 10);
    },
  },
  mounted(){
    this.timer = setInterval(()=>{
      this.date = new Date();
    }, 1000);
  },

};
</script>

<style>
  body{
    padding: 0;
    margin: 0;
    -webkit-box-sizing: content-box;
    -moz-box-sizing: content-box;
    box-sizing: content-box;
  }
#app {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  display: flex;
  flex-wrap: nowrap;
  flex-direction: row;
  justify-content: center;
}
</style>
