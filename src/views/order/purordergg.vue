<template>
  <el-table :data="purordergg"
            height="250"
            border
            style="width: 100%"
            :highlight-current-row='true'
            :show-summary='true'
            sum-text='合计'
            header-row-class-name="ft-gtable-header-row">
    <el-table-column prop="operator"
                     label="操作"
                     width="140">
      <template slot-scope="scope">
        <el-button type="primary"
                   icon="el-icon-check"
                   size='mini'></el-button>
        <el-button type="primary"
                   icon="el-icon-delete"
                   size='mini'></el-button>
      </template>
    </el-table-column>
    <el-table-column prop="feetype"
                     label="费用类型"
                     width="180">
    </el-table-column>
    <el-table-column prop="datetype"
                     label="日期方式">
    </el-table-column>
    <el-table-column prop="fcy"
                     label="金额">
    </el-table-column>
    <el-table-column prop="rdate"
                     label="预计收款日期">
    </el-table-column>
  </el-table>
</template>
<script>
export default {
  props: {
    gicode: String
  },
  data () {
    return {
      purordergg: [],
      allPurordergg: [{
        purordgicode: '1000',
        purordggicode: '1000',
        feetype: "预付款0",
        datetype: "日期前",
        fcy: "12132.2",
        rdate: "2019-01-01"
      }, {
        purordgicode: '1000',
        purordggicode: '1001',
        feetype: "预付款1",
        datetype: "日期前",
        fcy: "12132.2",
        rdate: "2019-01-01"
      }, {
        purordgicode: '1001',
        purordggicode: '1002',
        feetype: "预付款2",
        datetype: "日期前",
        fcy: "12132.2",
        rdate: "2019-01-01"
      }, {
        purordgicode: '1001',
        purordggicode: '1003',
        feetype: "预付款3",
        datetype: "日期前",
        fcy: "12132.2",
        rdate: "2019-01-01"
      }, {
        purordgicode: '1001',
        purordggicode: '1004',
        feetype: "预付款4",
        datetype: "日期前",
        fcy: "12132.2",
        rdate: "2019-01-01"
      }, {
        purordgicode: '1002',
        purordggicode: '1005',
        feetype: "预付款5",
        datetype: "日期前",
        fcy: "12132.2",
        rdate: "2019-01-01"
      }, {
        purordgicode: '1003',
        purordggicode: '1006',
        feetype: "预付款6",
        datetype: "日期前",
        fcy: "12132.2",
        rdate: "2019-01-01"
      }]
    }
  },
  watch: {
    gicode: function (val) {
      debugger
      this.purordergg = this.allPurordergg.filter((value, index) => value.purordgicode === val);
    }
  }
}
</script>

