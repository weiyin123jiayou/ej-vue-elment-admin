<template>
  <div class="productDetails">
    <h2>产品详情</h2>
    <el-button type="text" @click="backHandler">返回</el-button>
        <p><strong>产品名称</strong> {{product.name}} </p>
        <p><strong>产品单价</strong> {{product.price}}  </p>
        <p><strong>产品介绍</strong> {{product.description}}  </p>
        <p><strong>产品图片</strong> 
            <img :src="product.photo" alt="">
        </p>
  </div>
</template>
<script>
import {mapState,mapActions} from 'vuex'
export default {
  computed:{
      ...mapState('product',['product'])
  },
  created(){
    // console.log(this.$route);
    let id = this.$route.query.id;
    this.findProductById(id);
  },
  methods:{
      ...mapActions('product',['findProductById']),
      backHandler() {
      this.$router.go(-1)
    }
  }
}
</script>
<style scoped>


</style>