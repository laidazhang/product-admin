<template>
  <a-card :bordered="false">
    <detail-list title="基本信息" col=1>
      <detail-list-item term="名称">{{productData.title}}</detail-list-item>
      <detail-list-item term="状态"><span v-if="productData.status == 1">上架</span><span v-else-if="productData.status == -1">下架</span></detail-list-item>
      <detail-list-item term="库存">{{productData.storeQty}}</detail-list-item>
      <detail-list-item term="描述">{{productData.description}}</detail-list-item>
    </detail-list>
    <a-divider>图片展示</a-divider>
    <a-carousel arrows dotsClass="slick-dots slick-thumb">
      <a slot="customPaging" slot-scope="props">
        <img :src="getImgUrl(props.i)" />
      </a>
      <div v-for="item in 4">
        <img :src="baseUrl+'abstract0'+item+'.jpg'" />
      </div>
    </a-carousel>
    <a-divider style="margin-bottom: 32px;margin-top: 100px;"/>
  </a-card>
</template>

<script>
  import DetailList from '../../components/tool/DetailList'

  const DetailListItem = DetailList.Item

  const productData = {
    id: 1,
    title: '商品标题',
    status: 1,
    storeQty: 100,
    description: '我是商品描述信息啦啦啦啦啦我是商品描述信息啦啦啦啦啦我是商品描述信息啦啦啦啦啦我是商品描述信息啦啦啦啦啦我是商品描述信息啦啦啦啦啦'
  }

  const baseUrl = 'https://raw.githubusercontent.com/vueComponent/ant-design-vue/master/components/vc-slick/assets/img/react-slick/'

  export default {
    name: 'ProductDetail',
    components: {DetailListItem, DetailList},
    data () {
      return {
        productData,
        baseUrl
      }
    },
    methods: {
      getImgUrl(i) {
        return `${baseUrl}abstract0${i + 1}.jpg`
      }
    }
  }
</script>

<style scoped>
  .title {
    color: rgba(0, 0, 0, .85);
    font-size: 16px;
    font-weight: 500;
    margin-bottom: 16px;
  }

  /*
    ant-carousel
   */
  .ant-carousel >>> .slick-dots {
    height: auto
  }
  .ant-carousel >>> .slick-slide img{
    border: 5px solid #FFF;
    display: block;
    margin: auto;
    max-width: 80%;
  }
  .ant-carousel >>> .slick-thumb {
    bottom: -45px;
  }
  .ant-carousel >>> .slick-thumb li {
    width: 60px;
    height: 45px;
  }
  .ant-carousel >>> .slick-thumb li img {
    width: 100%;
    height: 100%;
    filter: grayscale(100%);
  }
  .ant-carousel >>> .slick-thumb li.slick-active img{
    filter: grayscale(0%);
  }
</style>
