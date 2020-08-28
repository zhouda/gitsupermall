<template>
  <div class="recommend">
    <div class="recommend-item" v-for="item in recommends" :key="item.acm">
      <a :href="item.link" >
        <img :src="item.image"/>
        <div>{{item.title}}</div>
      </a>
    </div>
  </div>
</template>

<script>
    export default {
      name: "RecommendView",
      props:{
          recommends:{
            type:Array,
            default(){
              return []
            }
          }
      }
    }
</script>

<style scoped>
.recommend{
  display: flex;
  text-align: center;
  padding: 10px 0  30px;
  font-size: 12px;
  border-bottom: solid 8px #eee;
}
.recommend-item{
    flex: 1;
  }
.recommend-item img{
  width: 70px;
  height: 70px;
  margin-bottom: 5px;
}
</style>
