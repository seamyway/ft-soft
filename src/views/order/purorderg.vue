<template>
  <div class='ft-gtable'>
    <el-table :data="purorderg"
              height="260"
              border
              style="width: 100%"
              @row-click='handleRowClick'
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
                       label="费用类型1"
                       width="180">
        <template slot="header"
                  slot-scope="scope">
          <el-input v-model="search"
                    size="mini"
                    placeholder="输入关键字搜索" />
        </template>
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
    <div class="ft-card">
      <el-row class='ft-card-title'>
        商品明细
      </el-row>
      <purordergg :gicode='currentPurordgicode'></purordergg>
    </div>
  </div>

</template>
<script>
import purordergg from './purordergg'
export default {
  components: { purordergg },
  data () {
    return {
      header: {
        props: ['item', 'headerClick', 'f_id'],
        render: function () {
          return (
            <span
              onClick={this.headerClick}
              class="customize_filter"
              id={this.f_id}
              style='cursor:pointer;display:inline-block'
            >
              <span style='padding-right:3px;'>{this.item.label}</span>
              <i class='el-icon-caret-bottom' />
            </span>
          )
        }
      },
      currentPurordgicode: '',
      purorderg: [{
        purordgicode: '1000',
        feetype: "预付款",
        datetype: "日期前",
        fcy: "12132.2",
        rdate: "2019-01-01"
      }, {
        purordgicode: '1001',
        feetype: "预付款",
        datetype: "日期前",
        fcy: "12132.2",
        rdate: "2019-01-01"
      }, {
        purordgicode: '1002',
        feetype: "预付款",
        datetype: "日期前",
        fcy: "12132.2",
        rdate: "2019-01-01"
      }, {
        purordgicode: '1003',
        feetype: "预付款",
        datetype: "日期前",
        fcy: "12132.2",
        rdate: "2019-01-01"
      }, {
        purordgicode: '1004',
        feetype: "预付款",
        datetype: "日期前",
        fcy: "12132.2",
        rdate: "2019-01-01"
      }, {
        purordgicode: '1005',
        feetype: "预付款",
        datetype: "日期前",
        fcy: "12132.2",
        rdate: "2019-01-01"
      }, {
        purordgicode: '1006',
        feetype: "预付款",
        datetype: "日期前",
        fcy: "12132.2",
        rdate: "2019-01-01"
      }]
    }
  },
  methods: {
    handleRowClick (row, event, column) {
      this.currentPurordgicode = row.purordgicode;
    }
  }
}
</script>

