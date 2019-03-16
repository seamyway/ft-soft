<template>
  <div class="ft-rtable purorder">
    <el-row class='ft-rtable-header'>
      <el-col :span='16'
              class='ft-rtable-title'>
        采购合同
      </el-col>
      <el-col :span='8'
              class='ft-rtable-tools'>
        <el-button-group>
          <el-button type="primary"
                     icon="el-icon-edit"
                     size="small">保存</el-button>
          <el-button type="primary"
                     icon="el-icon-delete"
                     size="small">删除</el-button>
          <el-button type="primary"
                     icon="el-icon-check"
                     size="small">提交</el-button>
        </el-button-group>
      </el-col>
    </el-row>
    <el-tabs type="border-card">
      <el-tab-pane class='ft-panel'
                   label="基本信息">
        <div class="ft-card">
          <el-row class='ft-card-title'>
            公共信息
          </el-row>
          <el-form class='ft-form'
                   :inline="true"
                   :model="purorder"
                   :rules="rules"
                   label-width='100px'
                   size="mini"
                   :label-position="labelPosition">
            <el-form-item label="采购合同号"
                          prop='purordcode'>
              <el-input v-model="purorder.purordcode"
                        placeholder="采购合同号"></el-input>
            </el-form-item>
            <el-form-item label="业务人员"
                          prop='bcode'>
              <el-input v-model="purorder.bcode"
                        placeholder="业务人员"></el-input>
            </el-form-item>
            <el-form-item label="公司"
                          prop='bcode'>
              <el-input v-model="purorder.corpbode"
                        placeholder="公司"></el-input>
            </el-form-item>
            <el-form-item label="银行名称">
              <el-input v-model="purorder.account"
                        placeholder="银行名称"></el-input>
            </el-form-item>
          </el-form>
        </div>
        <div class="ft-card">
          <el-row class='ft-card-title'>
            基本信息
          </el-row>
          <el-form class='ft-form'
                   :inline="true"
                   :model="purorder"
                   :rules="rules"
                   label-width='100px'
                   size="mini"
                   :label-position="labelPosition">
            <el-form-item label="客户"
                          prop='ccode'>
              <el-input v-model="purorder.ccode"></el-input>
            </el-form-item>
            <el-form-item label="客户联系人"
                          prop='ccodedesc'>
              <el-input v-model="purorder.ccodedesc"></el-input>
            </el-form-item>
            <el-form-item label="贸易国别"
                          prop='ncode'>
              <el-input v-model="purorder.ncode"></el-input>
            </el-form-item>
            <el-form-item label="签约日期">
              <el-input v-model="purorder.rdate"></el-input>
            </el-form-item>
          </el-form>
        </div>
        <div class="ft-card">
          <el-row class='ft-card-title'>
            收汇方式
          </el-row>
          <purorderg></purorderg>
        </div>
        <sysinfo :purorder='purorder'></sysinfo>
      </el-tab-pane>
      <el-tab-pane label="银行账号">
        <div class="ft-card">
          <el-row class='ft-card-title'>
            银行账号
          </el-row>
          <gridTable :data='data'
                     :columnConfig='columnConfig'></gridTable>
        </div>
      </el-tab-pane>
      <el-tab-pane label="附件管理">角色管理</el-tab-pane>
    </el-tabs>
  </div>
</template>
<script>
import purorderg from './purorderg'
import sysinfo from '../common/sysinfo'
import gridTable from '../common/gridTable/gridTable'

export default {
  data () {
    return {
      labelPosition: 'left',
      purorder: {
        purordicode: '',
        purordcode: ''
      },
      rules: {
        purordcode: [{ required: true, message: '请输入合同号', trigger: 'blur' },
        { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }],
        ccode: [{ required: true, message: '请输入ccode', trigger: 'blur' }]
      },
      data: [{
        bankCode: '1001',
        bankName: '中国工商银行',
        rdate: '2019-01-01'
      }, {
        bankCode: '1002',
        bankName: '中国农业银行',
        rdate: '2019-01-02'
      }, {
        bankCode: '1003',
        bankName: '中国建设银行',
        rdate: '2019-01-03'
      }, {
        bankCode: '1004',
        bankName: '中国交通银行',
        rdate: '2019-01-04'
      }
      ],
      columnConfig: [{
        prop: 'bankCode',
        label: "银行账号",
        width: '180px'
      }, {
        prop: 'bankName',
        label: "银行名称",
        width: '180px'
      }, {
        prop: 'rdate',
        label: "开户时间",
        width: '280px'
      }]
    }
  },
  components: { purorderg, sysinfo, gridTable }
}
</script>
<style lang='scss'>
</style>


