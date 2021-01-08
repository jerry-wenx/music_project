<template>
  <div class="Recommend">
    <Title>推荐歌单</Title>
    <ul class="recommendList">
      <router-link
        v-for="rem in recommendMusicList"
        :key="rem.id"
        to="/"
        tag="li"
      >
        <div>
          <img :src="rem.picUrl" />
          <span>{{ rem.playCount | formatNum }}</span>
        </div>
        <p>{{ rem.name }}</p>
      </router-link>
    </ul>
     <Title>最新音乐</Title>
     <MusicItem :newMusicList='newMusicList'></MusicItem>

     <div class="footer"></div>
  </div>
</template>

<script>
import Title from "../components/Title";
import MusicItem from '../components/MusicItem';
export default {
  name: "Recommend",
  components: { 
    Title,
    MusicItem
  },
  data() {
    return {
      recommendMusicList: [],
      newMusicList: [],
    };
  },
  beforeRouteEnter(to, from, next) {
    next((vm) => {
      vm.$http.get("/personalized?limit=6").then((data) => {
        // console.log(data);
        vm.recommendMusicList = data.data.result;
      });
      vm.$http.get("/personalized/newsong").then((data) => {
        // console.log(data);
        vm.newMusicList = data.data.result;
      });
    });
  },
  filters: {
    formatNum(value) {
      return (value / 10000).toFixed(1) + "万";
    },
  },
};
</script>


<style lang="less" scoped>
ul.recommendList {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  font-size: 14px;
  li {
    width: 33%;
    margin-bottom: 15px;
    div {
      position: relative;
      img {
        display: block;
      }
      span {
        font-size: 12px;
        position: absolute;
        right: 5px;
        top: 2px;
        color: #fff;
        text-shadow: 1px 1px 10px #000;
      }
    }
  }
  p {
    text-align: left;
    padding: 0 8px;
    display: -webkit-box;
    display: -moz-box;
    white-space: pre-wrap;
    word-wrap: break-word;
    overflow: hidden;
    text-overflow: ellipsis;
    -webkit-box-orient: vertical;
    -webkit-line-clamp: 2;
  }
}
.footer {
  height: 200px;
  background: url("../assets/footerbg.png") no-repeat;
}
</style>
