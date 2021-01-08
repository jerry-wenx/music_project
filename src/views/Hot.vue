<template>
  <div class="hot">
    <div class="bg">
      <span></span>
      <p>更新日期: {{ time }}</p>
    </div>

    <MusicItem></MusicItem>
  </div>
</template>


<script>
import MusicItem from "../components/MusicItem";
export default {
  name: "Hot",
  components: {
    MusicItem,
  },
  data() {
    return {
      hotMusicList: [],
      time: "",
    };
  },
  mounted() {
    let datatime = new Date();
    let m = datatime.getMonth() + 1;
    m = m > 10 ? m : "0" + m;
    let d = datatime.getDate();
    d = d > 10 ? d : "0" + d;
    this.time = m + "月 " + d + "日";
  },
  beforeRouteEnter(to, from, next) {
    next((vm) => {
      vm.$http.get("/playlist/hot").then((data) => {
        console.log(data);
      });
    });
  },
};
</script>



<style lang="less" scoped>
.bg {
  width: 100%;
  height: 145px;
  background: url("../assets/hotbg.jpg");
  overflow: hidden;
  background-size: cover;
  span {
    display: block;
    margin: 30px 0 0 10px;
    width: 142px;
    height: 70px;
    background: url("../assets/bofang.png") no-repeat -21px -28px/166px 97px;
  }
  p {
    margin-top: 3px;
    font-size: 12px;
    color: #fff;
    text-align: left;
    margin-left: 12px;
  }
}
</style>