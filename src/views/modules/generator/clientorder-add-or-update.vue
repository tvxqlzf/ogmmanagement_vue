<template>
  <el-dialog
    :title="!dataForm.id ? '新增' : '修改'"
    :close-on-click-modal="false"
    :visible.sync="visible">
    <el-form :model="dataForm" :rules="dataRule" ref="dataForm" @keyup.enter.native="dataFormSubmit()" label-width="80px">
    <el-form-item label="下单公司id" prop="compId">
      <el-input v-model="dataForm.compId" placeholder="下单公司id"></el-input>
    </el-form-item>
    <el-form-item label="被下单员工编号" prop="engId">
      <el-input v-model="dataForm.engId" placeholder="被下单员工编号"></el-input>
    </el-form-item>
    <el-form-item label="订单状态" prop="orderStatus">
      <el-input v-model="dataForm.orderStatus" placeholder="订单状态"></el-input>
    </el-form-item>
    <el-form-item label="项目编号" prop="pId">
      <el-input v-model="dataForm.pId" placeholder="项目编号"></el-input>
    </el-form-item>
    </el-form>
    <span slot="footer" class="dialog-footer">
      <el-button @click="visible = false">取消</el-button>
      <el-button type="primary" @click="dataFormSubmit()">确定</el-button>
    </span>
  </el-dialog>
</template>

<script>
  export default {
    data () {
      return {
        visible: false,
        dataForm: {
          orderId: 0,
          compId: '',
          engId: '',
          orderStatus: '',
          pId: ''
        },
        dataRule: {
          compId: [
            { required: true, message: '下单公司id不能为空', trigger: 'blur' }
          ],
          engId: [
            { required: true, message: '被下单员工编号不能为空', trigger: 'blur' }
          ],
          orderStatus: [
            { required: true, message: '订单状态不能为空', trigger: 'blur' }
          ],
          pId: [
            { required: true, message: '项目编号不能为空', trigger: 'blur' }
          ]
        }
      }
    },
    methods: {
      init (id) {
        this.dataForm.orderId = id || 0
        this.visible = true
        this.$nextTick(() => {
          this.$refs['dataForm'].resetFields()
          if (this.dataForm.orderId) {
            this.$http({
              url: this.$http.adornUrl(`/generator/clientorder/info/${this.dataForm.orderId}`),
              method: 'get',
              params: this.$http.adornParams()
            }).then(({data}) => {
              if (data && data.code === 0) {
                this.dataForm.compId = data.clientorder.compId
                this.dataForm.engId = data.clientorder.engId
                this.dataForm.orderStatus = data.clientorder.orderStatus
                this.dataForm.pId = data.clientorder.pId
              }
            })
          }
        })
      },
      // 表单提交
      dataFormSubmit () {
        this.$refs['dataForm'].validate((valid) => {
          if (valid) {
            this.$http({
              url: this.$http.adornUrl(`/generator/clientorder/${!this.dataForm.orderId ? 'save' : 'update'}`),
              method: 'post',
              data: this.$http.adornData({
                'orderId': this.dataForm.orderId || undefined,
                'compId': this.dataForm.compId,
                'engId': this.dataForm.engId,
                'orderStatus': this.dataForm.orderStatus,
                'pId': this.dataForm.pId
              })
            }).then(({data}) => {
              if (data && data.code === 0) {
                this.$message({
                  message: '操作成功',
                  type: 'success',
                  duration: 1500,
                  onClose: () => {
                    this.visible = false
                    this.$emit('refreshDataList')
                  }
                })
              } else {
                this.$message.error(data.msg)
              }
            })
          }
        })
      }
    }
  }
</script>
