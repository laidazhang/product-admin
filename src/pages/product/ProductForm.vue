<template>
  <a-card :body-style="{padding: '24px 32px'}" :bordered="false">
    <a-form>
      <a-form-item
        label="商品标题"
        :labelCol="{span: 2}"
        :wrapperCol="{span: 10}"
      >
        <a-input placeholder="给目标起个名字"/>
      </a-form-item>
      <a-form-item
        label="库存数量"
        :labelCol="{span: 2}"
        :wrapperCol="{span: 10}"
      >
        <a-input placeholder="100"/>
      </a-form-item>
      <a-form-item
        label="产地"
        :labelCol="{span: 2}"
        :wrapperCol="{span: 10}"
      >
        <a-cascader :options="cityList" @change="cityChange" :defaultValue="['福建省', '厦门市', '思明区']"/>
      </a-form-item>
      <a-form-item
        label="商品描述"
        :labelCol="{span: 2}"
        :wrapperCol="{span: 10}"
      >
        <a-textarea rows="4" placeholder="请输入你阶段性工作目标"/>
      </a-form-item>
      <a-form-item
        label="商品图片"
        :labelCol="{span: 2}"
        :wrapperCol="{span: 12}"
      >
        <div class="clearfix">
          <a-upload
            action="//jsonplaceholder.typicode.com/posts/"
            listType="picture-card"
            :fileList="fileList"
            @preview="handlePreview"
            @change="handleChange"
          >
            <div>
              <a-icon type="plus"/>
              <div class="ant-upload-text">Upload</div>
            </div>
          </a-upload>
          <a-modal :visible="previewVisible" :footer="null" @cancel="handleCancel">
            <img alt="example" style="width: 100%" :src="previewImage"/>
          </a-modal>
        </div>
      </a-form-item>
      <a-form-item :wrapperCol="{span: 10, offset: 7}">
        <a-button type="primary">提交</a-button>
        <a-button style="margin-left: 8px">保存</a-button>
      </a-form-item>
    </a-form>
  </a-card>
</template>

<script>
import AFormItem from 'ant-design-vue/es/form/FormItem'

export default {
  name: 'ProductForm',
  components: {AFormItem},
  data () {
    return {
      previewVisible: false,
      previewImage: '',
      fileList: [{
        uid: '-1',
        name: 'xxx.png',
        status: 'done',
        url: 'https://zos.alipayobjects.com/rmsportal/jkjgkEfvpUPVyRjUImniVslZfWPnJuuZ.png'
      }],
      cityList: [{
        value: '福建省',
        label: '福建省',
        children: [{
          value: '厦门市',
          label: '厦门市',
          children: [{
            value: '湖里区',
            label: '湖里区'
          },
          {
            value: '思明区',
            label: '思明区'
          }]
        },
        {
          value: '福州市',
          label: '福州市',
          children: [{
            value: '鼓楼区',
            label: '鼓楼区'
          },
          {
            value: '仓山区',
            label: '仓山区'
          }]
        }]
      }]
    }
  },
  methods:
      {
        handleCancel () {
          this.previewVisible = false
        },
        handlePreview (file) {
          this.previewImage = file.url || file.thumbUrl
          this.previewVisible = true
        },
        handleChange ({fileList}) {
          this.fileList = fileList
        },
        cityChange (value) {
          console.log(value)
        }
      }
}
</script>

<style scoped>
  .ant-upload-select-picture-card i {
    font-size: 32px;
    color: #999;
  }

  .ant-upload-select-picture-card .ant-upload-text {
    margin-top: 8px;
    color: #666;
  }
</style>
