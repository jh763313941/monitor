<template>
  <div id="index">
    <div class="bg flex-column">
      <div class="header">
        <h1>佛山市禅城区智慧公园指挥中心</h1>
      </div>
      <div class="body">
        <div class="parkLeft">
          <div class="topTitle flex-center">
            <img src="@/assets/images/more.svg"
                 alt="">
            佛山禅城智慧公园-全貌
          </div>
        </div>
        <div class="parkCenter">

        </div>
        <div class="parkRight">
          <div>
            {{dateYear}}{{dateDay}}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { formatTime } from '../utils/index.js'
export default {
  data() {
    return {
      loading: true,
      dateDay: null,
      dateYear: null,
      dateWeek: null,
      weekday: ["周日", "周一", "周二", "周三", "周四", "周五", "周六"],
    };
  },
  components: {

  },
  mounted() {
    // this.timeFn();
    this.cancelLoading();
    this.dateDay = formatTime(new Date(), 'HH: mm: ss');
    this.dateYear = formatTime(new Date(), 'yyyy-MM-dd');
  },
  methods: {
    timeFn() {
      setInterval(() => {
        this.dateDay = formatTime(new Date(), 'HH: mm: ss');
        this.dateYear = formatTime(new Date(), 'yyyy-MM-dd');
        this.dateWeek = this.weekday[new Date().getDay()];
      }, 1000)
    },
    cancelLoading() {
      setTimeout(() => {
        this.loading = false;
      }, 500);
    }
  }
};
</script>

<style lang="scss">
@import "../assets/scss/index.scss";
</style>