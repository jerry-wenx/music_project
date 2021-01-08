<template>
  <div class="topnav"> 
      <ul class='top'>
        <li><router-link to="/">推荐音乐</router-link></li>
        <li><router-link to="/hot">热歌榜</router-link></li>
        <li><router-link to="/search">搜索</router-link></li>
      </ul>
  
  </div>
</template>



<style lang="less" scoped>
  .top {
    display: flex;
    border-bottom: 1px solid #ddd;
    li {
      flex: 1;
      line-height: 40px;
      a {
        display: inline-block;
        color: #000;
        text-decoration: none;
       
        &.router-link-exact-active {
        color: red;
         border-bottom: 2px solid red;
        }
      }
      
    }
  }
</style>
