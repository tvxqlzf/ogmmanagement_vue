<template>
  <el-dialog
    :title="!dataForm.id ? '追加' : '修改'"
    :close-on-click-modal="false"
    :visible.sync="visible">
    <el-form :model="dataForm" :rules="dataRule" ref="dataForm" @keyup.enter.native="dataFormSubmit()" label-width="80px">
    <el-form-item label="会社番号" label-width="120px" prop="engComp">
      <el-input v-model="dataForm.engComp" placeholder="会社番号"></el-input>
    </el-form-item>
    <el-form-item label="名前" label-width="120px" prop="engName">
      <el-input v-model="dataForm.engName" placeholder="名前"></el-input>
    </el-form-item>
    <el-form-item label="パスワード" label-width="120px" prop="engPasw">
      <el-input v-model="dataForm.engPasw" placeholder="パスワード"></el-input>
    </el-form-item>
    <el-form-item label="性別" label-width="120px" prop="engSex">
      <el-input v-model="dataForm.engSex" placeholder="性別"></el-input>
    </el-form-item>
    <el-form-item label="年齢" label-width="120px" prop="engAge">
      <el-input v-model="dataForm.engAge" placeholder="年齢"></el-input>
    </el-form-item>
    <el-form-item label="誕生日" label-width="120px" prop="engBirthday">
      <el-input v-model="dataForm.engBirthday" placeholder="誕生日"></el-input>
    </el-form-item>
    <el-form-item label="住所" label-width="120px" prop="engAddress">
      <el-input v-model="dataForm.engAddress" placeholder="住所"></el-input>
    </el-form-item>
    <el-form-item label="最寄り駅" label-width="120px" prop="engStation">
      <el-input v-model="dataForm.engStation" placeholder="最寄り駅"></el-input>
    </el-form-item>
    <el-form-item label="電話番号" label-width="120px" prop="engPhone">
      <el-input v-model="dataForm.engPhone" placeholder="電話番号"></el-input>
    </el-form-item>
    <el-form-item label="メールアドレス" label-width="120px" prop="engEmail">
      <el-input v-model="dataForm.engEmail" placeholder="メールアドレス"></el-input>
    </el-form-item>
    <el-form-item label="社員番号" label-width="120px" prop="engNo">
      <el-input v-model="dataForm.engNo" placeholder="社員番号"></el-input>
    </el-form-item>
    <el-form-item label="口座番号" label-width="120px" prop="engBank">
      <el-input v-model="dataForm.engBank" placeholder="口座番号"></el-input>
    </el-form-item>
    <el-form-item label="履歴書" label-width="120px" prop="engResume">
      <el-input v-model="dataForm.engResume" placeholder="履歴書"></el-input>
    </el-form-item>
    <el-form-item label="自己PR" label-width="120px" prop="engJpr">
      <el-input v-model="dataForm.engJpr" placeholder="自己PR"></el-input>
    </el-form-item>
    <el-form-item label="スキル" label-width="120px" prop="engSkill">
      <el-input v-model="dataForm.engSkill" placeholder="スキル"></el-input>
    </el-form-item>
    <el-form-item label="経験年数" label-width="120px" prop="engExpyears">
      <el-input v-model="dataForm.engExpyears" placeholder="経験年数"></el-input>
    </el-form-item>
    <el-form-item label="国籍" label-width="120px" prop="engCountry">
      <el-input v-model="dataForm.engCountry" placeholder="国籍"></el-input>
    </el-form-item>
    <el-form-item label="入社日" label-width="120px" prop="engJoindate">
      <el-input v-model="dataForm.engJoindate" placeholder="入社日"></el-input>
    </el-form-item>
    <el-form-item label="会社PR" label-width="120px" prop="engCpr">
      <el-input v-model="dataForm.engCpr" placeholder="会社PR"></el-input>
    </el-form-item>
    <el-form-item label="希望賃金" label-width="120px" prop="engHopewage">
      <el-input v-model="dataForm.engHopewage" placeholder="希望賃金"></el-input>
    </el-form-item>
    <el-form-item label="契約賃金" label-width="120px" prop="engDeedwage">
      <el-input v-model="dataForm.engDeedwage" placeholder="契約賃金"></el-input>
    </el-form-item>
    <el-form-item label="日本語レベル" label-width="120px" prop="engJplevel">
      <el-input v-model="dataForm.engJplevel" placeholder="日本語レベル"></el-input>
    </el-form-item>
    <el-form-item label="来日日付" label-width="120px" prop="engCjpdate">
      <el-input v-model="dataForm.engCjpdate" placeholder="来日日付"></el-input>
    </el-form-item>
    <el-form-item label="保険ステータス" label-width="120px" prop="inStatus">
      <el-input v-model="dataForm.inStatus" placeholder="保険ステータス"></el-input>
    </el-form-item>
    <el-form-item label="保険レベル" label-width="120px" prop="inLevel">
      <el-input v-model="dataForm.inLevel" placeholder="保険レベル"></el-input>
    </el-form-item>
    <el-form-item label="緊急連絡人" label-width="120px" prop="engConname">
      <el-input v-model="dataForm.engConname" placeholder="緊急連絡人"></el-input>
    </el-form-item>
    <el-form-item label="緊急連絡先" label-width="120px" prop="engConphone">
      <el-input v-model="dataForm.engConphone" placeholder="緊急連絡先"></el-input>
    </el-form-item>
    <el-form-item label="在職ステータス" label-width="120px" prop="engStatus">
      <el-input v-model="dataForm.engStatus" placeholder="在職ステータス"></el-input>
    </el-form-item>
    <el-form-item label="退社日" label-width="120px" prop="engResigndate">
      <el-input v-model="dataForm.engResigndate" placeholder="退社日"></el-input>
    </el-form-item>
    <el-form-item label="扶養人数" label-width="120px" prop="engRaise">
      <el-input v-model="dataForm.engRaise" placeholder="扶養人数"></el-input>
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
            { required: true, message: '会社番号は必須項目です！', trigger: 'blur' }
          ],
          engName: [
            { required: true, message: '名前は必須項目です！', trigger: 'blur' }
          ],
          engPasw: [
            { required: true, message: 'パスワードは必須項目です！', trigger: 'blur' }
          ],
          engSex: [
            { required: true, message: '性別は必須項目です！', trigger: 'blur' }
          ],
          engAge: [
            { required: true, message: '年齢は必須項目です！', trigger: 'blur' }
          ],
          engBirthday: [
            { required: true, message: '誕生日は必須項目です！', trigger: 'blur' }
          ],
          engAddress: [
            { required: true, message: '住所は必須項目です！', trigger: 'blur' }
          ],
          engStation: [
            { required: true, message: '最寄り駅は必須項目です！', trigger: 'blur' }
          ],
          engPhone: [
            { required: true, message: '電話番号は必須項目です！', trigger: 'blur' }
          ],
          engEmail: [
            { required: true, message: 'メールアドレスは必須項目です！', trigger: 'blur' }
          ],
          engNo: [
            { required: true, message: '社員番号は必須項目です！', trigger: 'blur' }
          ],
          engBank: [
            { required: true, message: '口座番号は必須項目です！', trigger: 'blur' }
          ],
          engResume: [
            { required: true, message: '履歴書は必須項目です！', trigger: 'blur' }
          ],
          engJpr: [
            { required: true, message: '自己PRは必須項目です！', trigger: 'blur' }
          ],
          engSkill: [
            { required: true, message: 'スキルは必須項目です！', trigger: 'blur' }
          ],
          engExpyears: [
            { required: true, message: '経験年数は必須項目です！', trigger: 'blur' }
          ],
          engCountry: [
            { required: true, message: '国籍は必須項目です！', trigger: 'blur' }
          ],
          engJoindate: [
            { required: true, message: '入社日は必須項目です！', trigger: 'blur' }
          ],
          engCpr: [
            { required: true, message: '会社PRは必須項目です！', trigger: 'blur' }
          ],
          engHopewage: [
            { required: true, message: '希望賃金は必須項目です！', trigger: 'blur' }
          ],
          engDeedwage: [
            { required: true, message: '契約賃金は必須項目です！', trigger: 'blur' }
          ],
          engJplevel: [
            { required: true, message: '日本語レベルは必須項目です！', trigger: 'blur' }
          ],
          engCjpdate: [
            { required: true, message: '来日日付は必須項目です！', trigger: 'blur' }
          ],
          inStatus: [
            { required: true, message: '保険ステータスは必須項目です！', trigger: 'blur' }
          ],
          inLevel: [
            { required: true, message: '保険レベルは必須項目です！', trigger: 'blur' }
          ],
          engConname: [
            { required: true, message: '緊急連絡人は必須項目です！', trigger: 'blur' }
          ],
          engConphone: [
            { required: true, message: '緊急連絡先は必須項目です！', trigger: 'blur' }
          ],
          engStatus: [
            { required: true, message: '在職ステータスは必須項目です！', trigger: 'blur' }
          ],
          engResigndate: [
            { required: true, message: '退社日は必須項目です！', trigger: 'blur' }
          ],
          engRaise: [
            { required: true, message: '扶養人数は必須項目です！', trigger: 'blur' }
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

