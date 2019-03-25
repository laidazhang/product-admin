<template>
  <div class="standard-table">
    <a-table
      :bordered="bordered"
      :loading="loading"
      :columns="columns"
      :dataSource="dataSource"
      :pagination="pagination"
    >
      <template slot="operation" slot-scope="text, record">
        <a @click="toDetail(record.id)">详情</a>
        <a href="javascript:;">编辑</a>
        <a href="javascript:;">下架</a>
      </template>
    </a-table>
  </div>
</template>

<script>
export default {
  name: 'ProductTable',
  props: ['bordered', 'loading', 'columns', 'dataSource', 'rowKey', 'pagination'],
  data () {
    return {

    }
  },
  methods: {
    toDetail: function (id) {
      this.$router.push({ path: '/product/detail', query: { id: id }})
    }
  },
  created () {

  },
  watch: {

  }
}
</script>
