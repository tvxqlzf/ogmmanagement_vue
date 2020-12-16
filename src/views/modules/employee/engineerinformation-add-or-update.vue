<template>
  <el-dialog
    :title="!dataForm.id ? '新增' : '修改'"
    :close-on-click-modal="false"
    :visible.sync="visible">
    <el-form :model="dataForm" :rules="dataRule" ref="dataForm" @keyup.enter.native="dataFormSubmit()" label-width="80px">
    <el-form-item label="员工所属公司编号" prop="engComp">
      <el-input v-model="dataForm.engComp" placeholder="员工所属公司编号"></el-input>
    </el-form-item>
    <el-form-item label="员工姓名" prop="engName">
      <el-input v-model="dataForm.engName" placeholder="员工姓名"></el-input>
    </el-form-item>
    <el-form-item label="员工密码" prop="engPasw">
      <el-input v-model="dataForm.engPasw" placeholder="员工密码"></el-input>
    </el-form-item>
    <el-form-item label="员工性别" prop="engSex">
      <el-input v-model="dataForm.engSex" placeholder="员工性别"></el-input>
    </el-form-item>
    <el-form-item label="员工年龄" prop="engAge">
      <el-input v-model="dataForm.engAge" placeholder="员工年龄"></el-input>
    </el-form-item>
    <el-form-item label="员工生日" prop="engBirthday">
      <el-input v-model="dataForm.engBirthday" placeholder="员工生日"></el-input>
    </el-form-item>
    <el-form-item label="员工住址" prop="engAddress">
      <el-input v-model="dataForm.engAddress" placeholder="员工住址"></el-input>
    </el-form-item>
    <el-form-item label="员工最近车站" prop="engStation">
      <el-input v-model="dataForm.engStation" placeholder="员工最近车站"></el-input>
    </el-form-item>
    <el-form-item label="员工手机" prop="engPhone">
      <el-input v-model="dataForm.engPhone" placeholder="员工手机"></el-input>
    </el-form-item>
    <el-form-item label="员工邮箱" prop="engEmail">
      <el-input v-model="dataForm.engEmail" placeholder="员工邮箱"></el-input>
    </el-form-item>
    <el-form-item label="员工番号" prop="engNo">
      <el-input v-model="dataForm.engNo" placeholder="员工番号"></el-input>
    </el-form-item>
    <el-form-item label="员工银行账户" prop="engBank">
      <el-input v-model="dataForm.engBank" placeholder="员工银行账户"></el-input>
    </el-form-item>
    <el-form-item label="员工简历" prop="engResume">
      <el-input v-model="dataForm.engResume" placeholder="员工简历"></el-input>
    </el-form-item>
    <el-form-item label="员工自己PR" prop="engJpr">
      <el-input v-model="dataForm.engJpr" placeholder="员工自己PR"></el-input>
    </el-form-item>
    <el-form-item label="员工技能" prop="engSkill">
      <el-input v-model="dataForm.engSkill" placeholder="员工技能"></el-input>
    </el-form-item>
    <el-form-item label="员工经验年数" prop="engExpyears">
      <el-input v-model="dataForm.engExpyears" placeholder="员工经验年数"></el-input>
    </el-form-item>
    <el-form-item label="员工国籍" prop="engCountry">
      <el-input v-model="dataForm.engCountry" placeholder="员工国籍"></el-input>
    </el-form-item>
    <el-form-item label="员工入职日期" prop="engJoindate">
      <el-input v-model="dataForm.engJoindate" placeholder="员工入职日期"></el-input>
    </el-form-item>
    <el-form-item label="员工公司PR" prop="engCpr">
      <el-input v-model="dataForm.engCpr" placeholder="员工公司PR"></el-input>
    </el-form-item>
    <el-form-item label="员工希望单金" prop="engHopewage">
      <el-input v-model="dataForm.engHopewage" placeholder="员工希望单金"></el-input>
    </el-form-item>
    <el-form-item label="员工契约单金" prop="engDeedwage">
      <el-input v-model="dataForm.engDeedwage" placeholder="员工契约单金"></el-input>
    </el-form-item>
    <el-form-item label="员工日语等级" prop="engJplevel">
      <el-input v-model="dataForm.engJplevel" placeholder="员工日语等级"></el-input>
    </el-form-item>
    <el-form-item label="员工来日日期" prop="engCjpdate">
      <el-input v-model="dataForm.engCjpdate" placeholder="员工来日日期"></el-input>
    </el-form-item>
    <el-form-item label="员工保险状态" prop="inStatus">
      <el-input v-model="dataForm.inStatus" placeholder="员工保险状态"></el-input>
    </el-form-item>
    <el-form-item label="员工保险等级" prop="inLevel">
      <el-input v-model="dataForm.inLevel" placeholder="员工保险等级"></el-input>
    </el-form-item>
    <el-form-item label="员工紧急联络人姓名" prop="engConname">
      <el-input v-model="dataForm.engConname" placeholder="员工紧急联络人姓名"></el-input>
    </el-form-item>
    <el-form-item label="员工紧急联络人电话" prop="engConphone">
      <el-input v-model="dataForm.engConphone" placeholder="员工紧急联络人电话"></el-input>
    </el-form-item>
    <el-form-item label="员工在职状态" prop="engStatus">
      <el-input v-model="dataForm.engStatus" placeholder="员工在职状态"></el-input>
    </el-form-item>
    <el-form-item label="员工离职时间" prop="engResigndate">
      <el-input v-model="dataForm.engResigndate" placeholder="员工离职时间"></el-input>
    </el-form-item>
    <el-form-item label="员工抚养人数" prop="engRaise">
      <el-input v-model="dataForm.engRaise" placeholder="员工抚养人数"></el-input>
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
          engComp: '',
          engName: '',
          engPasw: '',
          engSex: '',
          engAge: '',
          engBirthday: '',
          engAddress: '',
          engStation: '',
          engPhone: '',
          engEmail: '',
          engNo: '',
          engBank: '',
          engResume: '',
          engJpr: '',
          engSkill: '',
          engExpyears: '',
          engCountry: '',
          engJoindate: '',
          engCpr: '',
          engHopewage: '',
          engDeedwage: '',
          engJplevel: '',
          engCjpdate: '',
          inStatus: '',
          inLevel: '',
          engConname: '',
          engConphone: '',
          engStatus: '',
          engResigndate: '',
          engRaise: ''
        },
        dataRule: {
          engComp: [
            { required: true, message: '员工所属公司编号不能为空', trigger: 'blur' }
          ],
          engName: [
            { required: true, message: '员工姓名不能为空', trigger: 'blur' }
          ],
          engPasw: [
            { required: true, message: '员工密码不能为空', trigger: 'blur' }
          ],
          engSex: [
            { required: true, message: '员工性别不能为空', trigger: 'blur' }
          ],
          engAge: [
            { required: true, message: '员工年龄不能为空', trigger: 'blur' }
          ],
          engBirthday: [
            { required: true, message: '员工生日不能为空', trigger: 'blur' }
          ],
          engAddress: [
            { required: true, message: '员工住址不能为空', trigger: 'blur' }
          ],
          engStation: [
            { required: true, message: '员工最近车站不能为空', trigger: 'blur' }
          ],
          engPhone: [
            { required: true, message: '员工手机不能为空', trigger: 'blur' }
          ],
          engEmail: [
            { required: true, message: '员工邮箱不能为空', trigger: 'blur' }
          ],
          engNo: [
            { required: true, message: '员工番号不能为空', trigger: 'blur' }
          ],
          engBank: [
            { required: true, message: '员工银行账户不能为空', trigger: 'blur' }
          ],
          engResume: [
            { required: true, message: '员工简历不能为空', trigger: 'blur' }
          ],
          engJpr: [
            { required: true, message: '员工自己PR不能为空', trigger: 'blur' }
          ],
          engSkill: [
            { required: true, message: '员工技能不能为空', trigger: 'blur' }
          ],
          engExpyears: [
            { required: true, message: '员工经验年数不能为空', trigger: 'blur' }
          ],
          engCountry: [
            { required: true, message: '员工国籍不能为空', trigger: 'blur' }
          ],
          engJoindate: [
            { required: true, message: '员工入职日期不能为空', trigger: 'blur' }
          ],
          engCpr: [
            { required: true, message: '员工公司PR不能为空', trigger: 'blur' }
          ],
          engHopewage: [
            { required: true, message: '员工希望单金不能为空', trigger: 'blur' }
          ],
          engDeedwage: [
            { required: true, message: '员工契约单金不能为空', trigger: 'blur' }
          ],
          engJplevel: [
            { required: true, message: '员工日语等级不能为空', trigger: 'blur' }
          ],
          engCjpdate: [
            { required: true, message: '员工来日日期不能为空', trigger: 'blur' }
          ],
          inStatus: [
            { required: true, message: '员工保险状态不能为空', trigger: 'blur' }
          ],
          inLevel: [
            { required: true, message: '员工保险等级不能为空', trigger: 'blur' }
          ],
          engConname: [
            { required: true, message: '员工紧急联络人姓名不能为空', trigger: 'blur' }
          ],
          engConphone: [
            { required: true, message: '员工紧急联络人电话不能为空', trigger: 'blur' }
          ],
          engStatus: [
            { required: true, message: '员工在职状态不能为空', trigger: 'blur' }
          ],
          engResigndate: [
            { required: true, message: '员工离职时间不能为空', trigger: 'blur' }
          ],
          engRaise: [
            { required: true, message: '员工抚养人数不能为空', trigger: 'blur' }
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
              url: this.$http.adornUrl(`/generator/engineerinformation/info/${this.dataForm.engId}`),
              method: 'get',
              params: this.$http.adornParams()
            }).then(({data}) => {
              if (data && data.code === 0) {
                this.dataForm.engComp = data.engineerinformation.engComp
                this.dataForm.engName = data.engineerinformation.engName
                this.dataForm.engPasw = data.engineerinformation.engPasw
                this.dataForm.engSex = data.engineerinformation.engSex
                this.dataForm.engAge = data.engineerinformation.engAge
                this.dataForm.engBirthday = data.engineerinformation.engBirthday
                this.dataForm.engAddress = data.engineerinformation.engAddress
                this.dataForm.engStation = data.engineerinformation.engStation
                this.dataForm.engPhone = data.engineerinformation.engPhone
                this.dataForm.engEmail = data.engineerinformation.engEmail
                this.dataForm.engNo = data.engineerinformation.engNo
                this.dataForm.engBank = data.engineerinformation.engBank
                this.dataForm.engResume = data.engineerinformation.engResume
                this.dataForm.engJpr = data.engineerinformation.engJpr
                this.dataForm.engSkill = data.engineerinformation.engSkill
                this.dataForm.engExpyears = data.engineerinformation.engExpyears
                this.dataForm.engCountry = data.engineerinformation.engCountry
                this.dataForm.engJoindate = data.engineerinformation.engJoindate
                this.dataForm.engCpr = data.engineerinformation.engCpr
                this.dataForm.engHopewage = data.engineerinformation.engHopewage
                this.dataForm.engDeedwage = data.engineerinformation.engDeedwage
                this.dataForm.engJplevel = data.engineerinformation.engJplevel
                this.dataForm.engCjpdate = data.engineerinformation.engCjpdate
                this.dataForm.inStatus = data.engineerinformation.inStatus
                this.dataForm.inLevel = data.engineerinformation.inLevel
                this.dataForm.engConname = data.engineerinformation.engConname
                this.dataForm.engConphone = data.engineerinformation.engConphone
                this.dataForm.engStatus = data.engineerinformation.engStatus
                this.dataForm.engResigndate = data.engineerinformation.engResigndate
                this.dataForm.engRaise = data.engineerinformation.engRaise
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
              url: this.$http.adornUrl(`/generator/engineerinformation/${!this.dataForm.engId ? 'save' : 'update'}`),
              method: 'post',
              data: this.$http.adornData({
                'engId': this.dataForm.engId || undefined,
                'engComp': this.dataForm.engComp,
                'engName': this.dataForm.engName,
                'engPasw': this.dataForm.engPasw,
                'engSex': this.dataForm.engSex,
                'engAge': this.dataForm.engAge,
                'engBirthday': this.dataForm.engBirthday,
                'engAddress': this.dataForm.engAddress,
                'engStation': this.dataForm.engStation,
                'engPhone': this.dataForm.engPhone,
                'engEmail': this.dataForm.engEmail,
                'engNo': this.dataForm.engNo,
                'engBank': this.dataForm.engBank,
                'engResume': this.dataForm.engResume,
                'engJpr': this.dataForm.engJpr,
                'engSkill': this.dataForm.engSkill,
                'engExpyears': this.dataForm.engExpyears,
                'engCountry': this.dataForm.engCountry,
                'engJoindate': this.dataForm.engJoindate,
                'engCpr': this.dataForm.engCpr,
                'engHopewage': this.dataForm.engHopewage,
                'engDeedwage': this.dataForm.engDeedwage,
                'engJplevel': this.dataForm.engJplevel,
                'engCjpdate': this.dataForm.engCjpdate,
                'inStatus': this.dataForm.inStatus,
                'inLevel': this.dataForm.inLevel,
                'engConname': this.dataForm.engConname,
                'engConphone': this.dataForm.engConphone,
                'engStatus': this.dataForm.engStatus,
                'engResigndate': this.dataForm.engResigndate,
                'engRaise': this.dataForm.engRaise
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
