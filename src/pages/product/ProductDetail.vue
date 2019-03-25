<template>
  <a-card :bordered="false">
    <detail-list title="商品详情">
      <detail-list-item term="名称">{{productData.title}}</detail-list-item>
      <detail-list-item term="状态"><span v-if="productData.status == 1">上架</span><span v-else-if="productData.status == -1">下架</span></detail-list-item>
      <detail-list-item term="库存">{{productData.storeQty}}</detail-list-item>
      <detail-list-item term="描述">{{productData.description}}</detail-list-item>
    </detail-list>
    <a-divider style="margin-bottom: 32px"/>
    <detail-list title="补充信息">
      <detail-list-item term="用户姓名">付小小</detail-list-item>
      <detail-list-item term="联系电话">18100000001</detail-list-item>
      <detail-list-item term="常用快递">菜鸟仓储</detail-list-item>
      <detail-list-item term="取货地址">浙江省杭州市西湖区万塘路19号</detail-list-item>
      <detail-list-item term="备注">无</detail-list-item>
    </detail-list>
    <a-divider style="margin-bottom: 32px"/>
  </a-card>
</template>

<script>
  import PageLayout from '../../layouts/PageLayout'
  import DetailList from '../../components/tool/DetailList'
  const DetailListItem = DetailList.Item

  const productData = {
    id: 1,
    title: '商品标题',
    status: 1,
    storeQty: 100,
    description: '我是商品描述信息啦啦啦啦啦'
  }

  export default {
    name: 'ProductDetail',
    components: {PageLayout, DetailListItem, DetailList},
    data () {
      return {
        productData
      }
    }
  }
</script>

<style lang="less" scoped>
  .title {
    color: rgba(0, 0, 0, .85);
    font-size: 16px;
    font-weight: 500;
    margin-bottom: 16px;
  }
</style>
