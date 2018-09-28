<template>
    <div class="DigitalSingle">
        <BaseOclock
            v-for="digit in digits"
            :short-deg="digit.shortDeg"
            :long-deg="digit.longDeg">
        </BaseOclock>
    </div>
</template>

<script>
import BaseOclock from './BaseOclock.vue';
import DigitalSingleMap from './DigitalSingleMap';

export default {
  name: 'DigitalSingle',
  props: {
    value: Number,
  },
  data() {
    return {
    };
  },
  computed: {
    digits() {
      return DigitalSingleMap[this.value];
    },
  },
  components: {
    BaseOclock,
  },
};
</script>

<style>
    .DigitalSingle{
        width: 204px;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
    }
</style>
