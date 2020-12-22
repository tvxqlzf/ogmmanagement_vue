<template>
  <el-dialog
    :title="!dataForm.id ? '新增' : '修改'"
    :close-on-click-modal="false"
    :visible.sync="visible">
    <el-form :model="dataForm" :rules="dataRule" ref="dataForm" @keyup.enter.native="dataFormSubmit()" label-width="80px">
    <el-form-item label="员工编号" prop="engId">
      <el-input v-model="dataForm.engId" placeholder="员工编号"></el-input>
    </el-form-item>
    <el-form-item label="年月" prop="attYm">
      <el-input v-model="dataForm.attYm" placeholder="年月"></el-input>
    </el-form-item>
    <el-form-item label="工作天数" prop="days">
      <el-input v-model="dataForm.days" placeholder="工作天数"></el-input>
    </el-form-item>
    <el-form-item label="工作总小时数" prop="hours">
      <el-input v-model="dataForm.hours" placeholder="工作总小时数"></el-input>
    </el-form-item>
    <el-form-item label="缺勤小时数" prop="leavehours">
      <el-input v-model="dataForm.leavehours" placeholder="缺勤小时数"></el-input>
    </el-form-item>
    <el-form-item label="普通加班小时数" prop="overtime">
      <el-input v-model="dataForm.overtime" placeholder="普通加班小时数"></el-input>
    </el-form-item>
    <el-form-item label="深夜小时数" prop="night">
      <el-input v-model="dataForm.night" placeholder="深夜小时数"></el-input>
    </el-form-item>
    <el-form-item label="休日小时数" prop="holidayover">
      <el-input v-model="dataForm.holidayover" placeholder="休日小时数"></el-input>
    </el-form-item>
    <el-form-item label="交通费" prop="traffic">
      <el-input v-model="dataForm.traffic" placeholder="交通费"></el-input>
    </el-form-item>
    <el-form-item label="交通凭证" prop="traPicture">
      <el-input v-model="dataForm.traPicture" placeholder="交通凭证"></el-input>
    </el-form-item>
    <el-form-item label="作业报告书" prop="work">
      <el-input v-model="dataForm.work" placeholder="作业报告书"></el-input>
    </el-form-item>
    <el-form-item label="时间表" prop="timetable">
      <el-input v-model="dataForm.timetable" placeholder="时间表"></el-input>
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
          attId: 0,
          engId: '',
          attYm: '',
          days: '',
          hours: '',
          leavehours: '',
          overtime: '',
          night: '',
          holidayover: '',
          traffic: '',
          traPicture: '',
          work: '',
          timetable: ''
        },
        dataRule: {
          engId: [
            { required: true, message: '员工编号不能为空', trigger: 'blur' }
          ],
          attYm: [
            { required: true, message: '年月不能为空', trigger: 'blur' }
          ],
          days: [
            { required: true, message: '工作天数不能为空', trigger: 'blur' }
          ],
          hours: [
            { required: true, message: '工作总小时数不能为空', trigger: 'blur' }
          ],
          leavehours: [
            { required: true, message: '缺勤小时数不能为空', trigger: 'blur' }
          ],
          overtime: [
            { required: true, message: '普通加班小时数不能为空', trigger: 'blur' }
          ],
          night: [
            { required: true, message: '深夜小时数不能为空', trigger: 'blur' }
          ],
          holidayover: [
            { required: true, message: '休日小时数不能为空', trigger: 'blur' }
          ],
          traffic: [
            { required: true, message: '交通费不能为空', trigger: 'blur' }
          ],
          traPicture: [
            { required: true, message: '交通凭证不能为空', trigger: 'blur' }
          ],
          work: [
            { required: true, message: '作业报告书不能为空', trigger: 'blur' }
          ],
          timetable: [
            { required: true, message: '时间表不能为空', trigger: 'blur' }
          ]
        }
      }
    },
    methods: {
      init (id) {
        this.dataForm.attId = id || 0
        this.visible = true
        this.$nextTick(() => {
          this.$refs['dataForm'].resetFields()
          if (this.dataForm.attId) {
            this.$http({
              url: this.$http.adornUrl(`/generator/attendance/info/${this.dataForm.attId}`),
              method: 'get',
              params: this.$http.adornParams()
            }).then(({data}) => {
              if (data && data.code === 0) {
                this.dataForm.engId = data.attendance.engId
                this.dataForm.attYm = data.attendance.attYm
                this.dataForm.days = data.attendance.days
                this.dataForm.hours = data.attendance.hours
                this.dataForm.leavehours = data.attendance.leavehours
                this.dataForm.overtime = data.attendance.overtime
                this.dataForm.night = data.attendance.night
                this.dataForm.holidayover = data.attendance.holidayover
                this.dataForm.traffic = data.attendance.traffic
                this.dataForm.traPicture = data.attendance.traPicture
                this.dataForm.work = data.attendance.work
                this.dataForm.timetable = data.attendance.timetable
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
              url: this.$http.adornUrl(`/generator/attendance/${!this.dataForm.attId ? 'save' : 'update'}`),
              method: 'post',
              data: this.$http.adornData({
                'attId': this.dataForm.attId || undefined,
                'engId': this.dataForm.engId,
                'attYm': this.dataForm.attYm,
                'days': this.dataForm.days,
                'hours': this.dataForm.hours,
                'leavehours': this.dataForm.leavehours,
                'overtime': this.dataForm.overtime,
                'night': this.dataForm.night,
                'holidayover': this.dataForm.holidayover,
                'traffic': this.dataForm.traffic,
                'traPicture': this.dataForm.traPicture,
                'work': this.dataForm.work,
                'timetable': this.dataForm.timetable
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
