<template>
  <div class="search">
    <p>
      <input type="text" placeholder="搜索歌曲、 歌手、 专辑" />
      <span></span>
    </p>
    <div class="text">热门搜索</div>
    <ul class="hotSearch">
        <router-link v-for="(item, index) in hotSearch" :key="index" to="/" tag="li">
            <!-- <div class="content"></div> -->{{item.first}}
        </router-link>
    </ul>
  </div>
</template>


<script>
export default {
    name: 'Search',
    data(){
        return {
            hotSearch: [],
        }
    },
    beforeRouteEnter(to,from,next){
        next(vm=>{
            vm.$http.get('/search/hot').then(data=>{
                console.log(data.data.result.hots);
                vm.hotSearch = data.data.result.hots;
            })
        })
    }
}
</script>

<style lang="less" scoped>
.search {
  p {
    position: relative;
    display: flex;
    height: 60px;
    border-bottom: 1px solid #ddd;
    justify-content: space-around;
    align-items: center;
    input {
      outline: none;
      border: 0;
      height: 30px;
      width: 95%;
      border-radius: 15px;
      background-color: #ebecec;
      text-indent: 30px;
    }
    span {
      display: block;
      width: 13px;
      height: 13px;
      background: url("../assets/fdj.svg");
      position: absolute;
      left: 20px;
    }
    }
    .text {
        font-size: 12px;
        color: #666;
        line-height: 30px;
        text-align: left;
        padding: 15px 10px 10px 10px;
    }
    .hotSearch {
      display: flex;
      flex-wrap: wrap;
      li {
        padding: 10px 15px;
        background-color: #ddd;
        margin: 5px 8px;
        border-radius: 30px;
      }
    }
}
</style>