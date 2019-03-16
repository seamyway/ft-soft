<template>
  <div class="ft-card">
    <el-row class='ft-card-title'>
      系统信息
    </el-row>
    <el-form class='ft-form'
             :model="purorder"
             :inline="true"
             label-width='100px'
             size="mini"
             label-position="left">
      <el-form-item label="创建人"
                    prop='creator'>
        <el-input v-model="purorder.creator"></el-input>
      </el-form-item>
      <el-form-item label="创建时间"
                    prop='createtime'>
        <el-input v-model="purorder.createtime"></el-input>
      </el-form-item>
      <el-form-item label="修改人"
                    prop='modifier'>
        <el-input v-model="purorder.modifier"></el-input>
      </el-form-item>
      <el-form-item label="修改时间"
                    prop='modifytime'>
        <el-input v-model="purorder.modifytime"></el-input>
      </el-form-item>
    </el-form>
  </div>
</template>
<script>
export default {
  props: {
    purorder: Object
  }
}
</script>

