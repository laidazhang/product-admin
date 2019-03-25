<template>
  <a-card>
    <div :class="advanced ? 'search' : null">
      <a-form layout="horizontal">
        <div :class="advanced ? null: 'fold'">
          <a-row >
          <a-col :md="8" :sm="24" >
            <a-form-item
              label="商品ID"
              :labelCol="{span: 5}"
              :wrapperCol="{span: 18, offset: 1}"
            >
              <a-input placeholder="请输入" />
            </a-form-item>
          </a-col>
          <a-col :md="8" :sm="24" >
            <a-form-item
              label="商品名称"
              :labelCol="{span: 5}"
              :wrapperCol="{span: 18, offset: 1}"
            >
            <a-input placeholder="请输入" />
            </a-form-item>
          </a-col>
          <a-col :md="8" :sm="24" >
            <a-form-item
              label="商品分类"
              :labelCol="{span: 5}"
              :wrapperCol="{span: 18, offset: 1}"
            >
              <a-select placeholder="请选择">
                <a-select-option value="1">水果</a-select-option>
                <a-select-option value="2">海鲜干货</a-select-option>
              </a-select>
            </a-form-item>
          </a-col>
        </a-row>
          <a-row v-if="advanced">
          <a-col :md="8" :sm="24" >
            <a-form-item
              label="商品状态"
              :labelCol="{span: 5}"
              :wrapperCol="{span: 18, offset: 1}"
            >
              <a-select placeholder="请选择">
                <a-select-option value="1">关闭</a-select-option>
                <a-select-option value="2">运行中</a-select-option>
              </a-select>
            </a-form-item>
          </a-col>
        </a-row>
        </div>
        <span style="float: right; margin-top: 3px;">
          <a-button type="primary">查询</a-button>
          <a-button @click="addNew" type="primary">新建</a-button>
          <a @click="toggleAdvanced" style="margin-left: 8px">
            {{advanced ? '收起' : '展开'}}
            <a-icon :type="advanced ? 'up' : 'down'" />
          </a>
        </span>
      </a-form>
    </div>
    <div>
      <product-table
        :columns="columns"
        :dataSource="dataSource"
      />
    </div>
  </a-card>
</template>

<script>
import ProductTable from '../../components/table/ProductTable'
import AInput from "ant-design-vue/es/input/Input";
const columns = [
  {
    title: '商品编号',
    dataIndex: 'id'
  },
  {
    title: '商品名称',
    dataIndex: 'title'
  },
  {
    title: '商品库存',
    dataIndex: 'storeQty',
    sorter: true
  },
  {
    title: '状态',
    dataIndex: 'status'
  },
  {
    title: '上架时间',
    dataIndex: 'createTime',
    sorter: true
  },
  {
    title: '操作',
    key: 'operation',
    scopedSlots: { customRender: 'operation' }
  }
]

const dataSource = []

for (let i = 0; i < 100; i++) {
  dataSource.push({
    key: i,
    id: i,
    title: '商品' + i,
    storeQty: Math.floor(Math.random() * 1000),
    status: Math.floor(Math.random() * 10) % 4,
    createTime: new Date().toLocaleDateString()
  })
}

export default {
  name: 'ProductList',
  components: {AInput, ProductTable},
  data () {
    return {
      advanced: true,
      columns: columns,
      dataSource: dataSource
    }
  },
  methods: {
    toggleAdvanced () {
      this.advanced = !this.advanced
    },
    addNew () {
      alert('add new row' + new Date())
      /*this.dataSource.unshift({
        key: this.dataSource.length,
        no: 'NO ' + this.dataSource.length,
        description: '这是一段描述',
        callNo: Math.floor(Math.random() * 1000),
        status: Math.floor(Math.random() * 10) % 4,
        updatedAt: '2018-07-26'
      })*/
    }
  }
}
</script>

<style lang="less" scoped>
  .search{
    margin-bottom: 54px;
  }
  .fold{
    width: calc(100% - 216px);
    display: inline-block
  }
  .operator{
    margin-bottom: 18px;
  }
  @media screen and (max-width: 900px) {
    .fold {
      width: 100%;
    }
  }
</style>
