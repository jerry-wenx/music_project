<template>
  <ul class="musiclist">
    <router-link v-for="item in newMusicList" :key="item.id" to="/" tag="li">
      <div class="left">
        <div>{{ item.name }}</div>
        <p><span></span> {{ item.name }}</p>
      </div>
      <div class="right">
          <span></span>
      </div>
    </router-link>
  </ul>
</template>

<script>
export default {
  props: {
    newMusicList: Array,
  },
};
</script>


<style lang="less" scoped>
.musiclist {
  padding-left: 5px;
  li {
    display: flex;
    justify-content: space-between;
    border-bottom: 1px solid #ddd;
    padding: 10px 0 5px 0;
    .left {
        text-align: left;
      div {
        font-size: 16px;
      }
      p {
        font-size: 12px;
        padding: 5px 0;
        span {
            display: inline-block;
            width: 12px;
            height: 8px;
            background-image:  url('../assets/bofang.png');
            background-size: 166px 97px;
        }
      }
    }
    .right {
        display: flex;
        align-items: center;

        span {
            display: block;
            width: 22px;
            height: 22px;
            background-image: url('../assets/bofang.png');
            background-position:  -24px 0;
            background-size: 166px 97px;  
            margin-right: 3px;   
        }
    }
  }
}
</style>