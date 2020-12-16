<template>
  <div class="tab-bar-item" @click="itemClick">
    <div v-if="isActive"><slot name="item-icon"></slot></div>
    <div v-else><slot name="item-icon-active"></slot></div>
    <div :style="activeStyle"><slot name="item-text"></slot></div>
  </div>
</template>

<script>
    export default {
      name: "TabBarItem",
      props:{
        path:String,
        activeColor:{
          type:String,
          default:'red'
        }
      },
      data() {
        return {

        }
      },
      methods:{
        itemClick() {
          this.$router.push(this.path)
        }
      },
      computed:{
        //判断当前路由是否为点击的路由，是则返回ture
        isActive() {
          return this.$route.path.indexOf(this.path) == -1
        },
        activeStyle() {
          return this.isActive ? {} : {color: this.activeColor}
        }
      }
    }
</script>

<style scoped>
  /*  均等分*/
  .tab-bar-item{
    flex: 1;
    text-align: center;
    height: 49px;
    vertical-align: middle;
  }
  .tab-bar-item img{
    width: 24px;
    height: 24px;
  }

</style>
