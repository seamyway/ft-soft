<template>
  <div class='ft-gtable'
       style="position:relative">
    <el-table :data="data"
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
      <template v-for="(item,index) in columnConfig">
        <el-table-column :prop="item.prop"
                         :label="item.label"
                         :width="item.width"
                         :key='index'
                         :render-header="renderHeader">
        </el-table-column>
      </template>
    </el-table>

    <!-- 注册的筛选器 -->
    <div>
      <template v-for="(item, key) in regfilters">
        <!-- 输入框选择器 -->
        <div :class="{'filterWrap': true, 'hideBg': item.hidebg}"
             v-show="showFilter"
             :key="key"
             :style="item.position">
          <div class="filterContainer">
            <component :key="key"
                       :is="item.component"
                       :data="item.data"
                       :filterkey="item.filterkey"
                       :listinfo="item.listinfo"
                       :refname="item.refname"
                       :cdata="item.cdata"
                       :myprops="item.myprops"
                       :placeholderstr="item.myplaceholder"
                       :unit="item.unit"
                       :ftn="item.ftn"
                       :customizedata="item.customizedata">
            </component>
          </div>
        </div>
      </template>
    </div>

  </div>
</template>
<script>
import searchFilter from '@/views/filters/search.vue'
export default {
  components: { searchFilter },
  props: {
    data: Array,
    columnConfig: Array
  },
  data () {
    return {
      showFilter: false,
      regfilters: [{
        component: searchFilter,
        position: { top: 0, left: 0 }
      }
      ]
    }
  },
  methods: {
    renderHeader (h, { column, $index }) {
      return (
        <span on-click={this.headerClick}
          id={column.property}
          style='cursor:pointer;display:inline-block' >
          <span style='padding-right:3px;'>{column.label}</span>
          <i class='el-icon-caret-bottom' />
        </span >
      )
    },
    headerClick (e) {
      const id = e.currentTarget.id;
      this.showFilter = true;
      //设置过滤框的绝对定位位置
      this.filterPosition(
        e.currentTarget.parentElement.parentElement,
        id
      )
      console.info("headerClick")
    },
    handleRowClick (row, event, column) {
      this.currentPurordgicode = row.purordgicode;
    },
    filterPosition (filterbar, filtertag) {
      var offsetLeft = filterbar.offsetLeft
      var offsetHeight = filterbar.offsetHeight
      this.$set(this.regfilters[0].position, 'top', offsetHeight - 10 + 'px')
      this.$set(this.regfilters[0].position, 'left', offsetLeft + 'px')
      console.info(this.regfilters)
    },
  }
}
</script>

<style>
.filterWrap {
  min-width: 100px;
  border: 1px solid #ebeef5;
  border-radius: 2px;
  background-color: #fff;
  box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1);
  box-sizing: border-box;
  margin: 2px 0;
  position: absolute;
  z-index: 9;
}
</style>
