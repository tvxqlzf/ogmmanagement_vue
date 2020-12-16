<template>
  <el-dialog
    :title="!dataForm.id ? '新增' : '修改'"
    :close-on-click-modal="false"
    :visible.sync="visible">
    <el-form :model="dataForm" :rules="dataRule" ref="dataForm" @keyup.enter.native="dataFormSubmit()" label-width="80px">
    <el-form-item label="入场时间" prop="startdate">
      <el-input v-model="dataForm.startdate" placeholder="入场时间"></el-input>
    </el-form-item>
    <el-form-item label="精算范围" prop="wagerange">
      <el-input v-model="dataForm.wagerange" placeholder="精算范围"></el-input>
    </el-form-item>
    <el-form-item label="单金" prop="price">
      <el-input v-model="dataForm.price" placeholder="单金"></el-input>
    </el-form-item>
    <el-form-item label="预定退场时间" prop="enddate">
      <el-input v-model="dataForm.enddate" placeholder="预定退场时间"></el-input>
    </el-form-item>
    <el-form-item label="营业状态" prop="busiStatus">
      <el-input v-model="dataForm.busiStatus" placeholder="营业状态"></el-input>
    </el-form-item>
    <el-form-item label="咨询总数" prop="advisoryNo">
      <el-input v-model="dataForm.advisoryNo" placeholder="咨询总数"></el-input>
    </el-form-item>
    <el-form-item label="面试总数" prop="interviewNo">
      <el-input v-model="dataForm.interviewNo" placeholder="面试总数"></el-input>
    </el-form-item>
    <el-form-item label="结果等待数" prop="resultWait">
      <el-input v-model="dataForm.resultWait" placeholder="结果等待数"></el-input>
    </el-form-item>
    <el-form-item label="待面试数" prop="interviewWait">
      <el-input v-model="dataForm.interviewWait" placeholder="待面试数"></el-input>
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
          engId: 0,
          startdate: '',
          wagerange: '',
          price: '',
          enddate: '',
          busiStatus: '',
          advisoryNo: '',
          interviewNo: '',
          resultWait: '',
          interviewWait: ''
        },
        dataRule: {
          startdate: [
            { required: true, message: '入场时间不能为空', trigger: 'blur' }
          ],
          wagerange: [
            { required: true, message: '精算范围不能为空', trigger: 'blur' }
          ],
          price: [
            { required: true, message: '单金不能为空', trigger: 'blur' }
          ],
          enddate: [
            { required: true, message: '预定退场时间不能为空', trigger: 'blur' }
          ],
          busiStatus: [
            { required: true, message: '营业状态不能为空', trigger: 'blur' }
          ],
          advisoryNo: [
            { required: true, message: '咨询总数不能为空', trigger: 'blur' }
          ],
          interviewNo: [
            { required: true, message: '面试总数不能为空', trigger: 'blur' }
          ],
          resultWait: [
            { required: true, message: '结果等待数不能为空', trigger: 'blur' }
          ],
          interviewWait: [
            { required: true, message: '待面试数不能为空', trigger: 'blur' }
          ]
        }
      }
    },
    methods: {
      init (id) {
        this.dataForm.engId = id || 0
        this.visible = true
        this.$nextTick(() => {
          this.$refs['dataForm'].resetFields()
          if (this.dataForm.engId) {
            this.$http({
              url: this.$http.adornUrl(`/generator/businessinformation/info/${this.dataForm.engId}`),
              method: 'get',
              params: this.$http.adornParams()
            }).then(({data}) => {
              if (data && data.code === 0) {
                this.dataForm.startdate = data.businessinformation.startdate
                this.dataForm.wagerange = data.businessinformation.wagerange
                this.dataForm.price = data.businessinformation.price
                this.dataForm.enddate = data.businessinformation.enddate
                this.dataForm.busiStatus = data.businessinformation.busiStatus
                this.dataForm.advisoryNo = data.businessinformation.advisoryNo
                this.dataForm.interviewNo = data.businessinformation.interviewNo
                this.dataForm.resultWait = data.businessinformation.resultWait
                this.dataForm.interviewWait = data.businessinformation.interviewWait
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
              url: this.$http.adornUrl(`/generator/businessinformation/${!this.dataForm.engId ? 'save' : 'update'}`),
              method: 'post',
              data: this.$http.adornData({
                'engId': this.dataForm.engId || undefined,
                'startdate': this.dataForm.startdate,
                'wagerange': this.dataForm.wagerange,
                'price': this.dataForm.price,
                'enddate': this.dataForm.enddate,
                'busiStatus': this.dataForm.busiStatus,
                'advisoryNo': this.dataForm.advisoryNo,
                'interviewNo': this.dataForm.interviewNo,
                'resultWait': this.dataForm.resultWait,
                'interviewWait': this.dataForm.interviewWait
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
