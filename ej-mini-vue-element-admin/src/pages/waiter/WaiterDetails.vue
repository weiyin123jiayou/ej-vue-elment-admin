<template>
  <div class="waiterDetails">
    <h2>员工详情</h2>
    <el-button size="small" type="text" @click="backHandler">返回</el-button>
    {{waiters}}
        <p><strong>员工姓名</strong> {{waiters.name}} </p>
        <p><strong>手机号码</strong> {{waiters.telphone}}  </p>
        <p><strong>居住地</strong> {{waiters.city}}  </p>
  </div>
</template>
<script>
import {mapState,mapActions} from 'vuex'
export default {
    computed:{
      ...mapState('waiters',['waiters'])
  },
  created(){
    // console.log(this.$route);
    let id = this.$route.query.id;
    this.findAllWaiters(id);
  },
  methods:{
      ...mapActions('waiters',['findAllWaiters']),
      backHandler() {
      this.$router.go(-1)
    }
  }

}
</script>
<style scoped>


</style>