<template>
  <div class="waiterDetails">
    <h2>员工详情</h2>
    <el-button size="small" type="text" @click="backHandler">返回</el-button>
    <el-tabs v-model="activeName">
      <el-tab-pane label="基本信息" name="info">
        <el-table :data="waiters" size="mini"  @selection-change="handleSelectionChange">
        <el-table-column prop="realname" label="姓名"></el-table-column>
        <el-table-column prop="photo" label="照片"></el-table-column>
      </el-table>
      </el-tab-pane>
      <el-tab-pane label="订单信息" name="orders">
        订单信息...
      </el-tab-pane>
      <el-tab-pane label="服务地址" name="address">
        <el-table :data="address">
          <el-table-column label="省" prop="province"></el-table-column>
          <el-table-column label="市" prop="city"></el-table-column>
          <el-table-column label="区" prop="area"></el-table-column>
          <el-table-column label="街道" prop="address"></el-table-column>
          <el-table-column label="手机号" prop="telephone"></el-table-column>
        </el-table>
      </el-tab-pane>
    </el-tabs>
  </div>
</template>
<script>
import {mapState,mapActions} from 'vuex'
export default {
  data(){
    return {
      activeName:"info"
    }
  },
  created(){
    console.log(this.$route);
    let id = this.$route.query.id;
    // 通过id查询顾客，订单，地址
    this.findAddressByWaiterId(id);
  },
  computed:{
    ...mapState("address",["address"])
  },
  methods:{
    ...mapActions("address",["findAddressByWaiterId"]),
    backHandler(){
      // this.$router.push("/waiter")
      this.$router.go(-1)
    },
    handleSelectionChange(val) {
      this.ids = val.map(item=>item.id);
    },
  }

}
</script>
<style scoped>


</style>