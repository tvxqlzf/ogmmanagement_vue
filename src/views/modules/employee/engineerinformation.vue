<template>
  <div class="mod-config">
    <el-form :inline="true" :model="dataForm" @keyup.enter.native="getDataList()">
      <el-form-item>
        <el-input v-model="dataForm.key" placeholder="参数名" clearable></el-input>
      </el-form-item>
      <el-form-item>
        <el-button @click="getDataList()">検索</el-button>
        <el-button @click="resetData()">条件を消す</el-button>
        <el-button  type="primary" @click="addOrUpdateHandle()">新增</el-button>
        <el-button  type="danger" @click="deleteHandle()" :disabled="dataListSelections.length <= 0">一括削除</el-button>
      </el-form-item>
    </el-form>
    <el-table
      :data="dataList"
      border
      v-loading="dataListLoading"
      @selection-change="selectionChangeHandle"
      style="width: 100%;">
      <el-table-column
        type="selection"
        header-align="center"
        align="center"
        width="50">
      </el-table-column>
      <el-table-column
        prop="engId"
        header-align="center"
        align="center"
        label="员工编号">
      </el-table-column>
      <el-table-column
        prop="engComp"
        header-align="center"
        align="center"
        label="员工所属公司编号">
      </el-table-column>
      <el-table-column
        prop="engName"
        header-align="center"
        align="center"
        label="员工姓名">
      </el-table-column>
      <el-table-column
        prop="engPasw"
        header-align="center"
        align="center"
        label="员工密码">
      </el-table-column>
      <el-table-column
        prop="engSex"
        header-align="center"
        align="center"
        label="员工性别">
      </el-table-column>
      <el-table-column
        prop="engAge"
        header-align="center"
        align="center"
        label="员工年龄">
      </el-table-column>
      <el-table-column
        prop="engBirthday"
        header-align="center"
        align="center"
        label="员工生日">
      </el-table-column>
      <el-table-column
        prop="engAddress"
        header-align="center"
        align="center"
        label="员工住址">
      </el-table-column>
      <el-table-column
        prop="engStation"
        header-align="center"
        align="center"
        label="员工最近车站">
      </el-table-column>
      <el-table-column
        prop="engPhone"
        header-align="center"
        align="center"
        label="员工手机">
      </el-table-column>
      <el-table-column
        prop="engEmail"
        header-align="center"
        align="center"
        label="员工邮箱">
      </el-table-column>
      <el-table-column
        prop="engNo"
        header-align="center"
        align="center"
        label="员工番号">
      </el-table-column>
      <el-table-column
        prop="engBank"
        header-align="center"
        align="center"
        label="员工银行账户">
      </el-table-column>
      <el-table-column
        prop="engResume"
        header-align="center"
        align="center"
        label="员工简历">
      </el-table-column>
      <el-table-column
        prop="engJpr"
        header-align="center"
        align="center"
        label="员工自己PR">
      </el-table-column>
      <el-table-column
        prop="engSkill"
        header-align="center"
        align="center"
        label="员工技能">
      </el-table-column>
      <el-table-column
        prop="engExpyears"
        header-align="center"
        align="center"
        label="员工经验年数">
      </el-table-column>
      <el-table-column
        prop="engCountry"
        header-align="center"
        align="center"
        label="员工国籍">
      </el-table-column>
      <el-table-column
        prop="engJoindate"
        header-align="center"
        align="center"
        label="员工入职日期">
      </el-table-column>
      <el-table-column
        prop="engCpr"
        header-align="center"
        align="center"
        label="员工公司PR">
      </el-table-column>
      <el-table-column
        prop="engHopewage"
        header-align="center"
        align="center"
        label="员工希望单金">
      </el-table-column>
      <el-table-column
        prop="engDeedwage"
        header-align="center"
        align="center"
        label="员工契约单金">
      </el-table-column>
      <el-table-column
        prop="engJplevel"
        header-align="center"
        align="center"
        label="员工日语等级">
      </el-table-column>
      <el-table-column
        prop="engCjpdate"
        header-align="center"
        align="center"
        label="员工来日日期">
      </el-table-column>
      <el-table-column
        prop="inStatus"
        header-align="center"
        align="center"
        label="员工保险状态">
      </el-table-column>
      <el-table-column
        prop="inLevel"
        header-align="center"
        align="center"
        label="员工保险等级">
      </el-table-column>
      <el-table-column
        prop="engConname"
        header-align="center"
        align="center"
        label="员工紧急联络人姓名">
      </el-table-column>
      <el-table-column
        prop="engConphone"
        header-align="center"
        align="center"
        label="员工紧急联络人电话">
      </el-table-column>
      <el-table-column
        prop="engStatus"
        header-align="center"
        align="center"
        label="员工在职状态">
      </el-table-column>
      <el-table-column
        prop="engResigndate"
        header-align="center"
        align="center"
        label="员工离职时间">
      </el-table-column>
      <el-table-column
        prop="engRaise"
        header-align="center"
        align="center"
        label="员工抚养人数">
      </el-table-column>
      <el-table-column
        fixed="right"
        header-align="center"
        align="center"
        width="150"
        label="操作">
        <template slot-scope="scope">
          <el-button type="text" size="small" @click="addOrUpdateHandle(scope.row.engId)">修改</el-button>
          <el-button type="text" size="small" @click="deleteHandle(scope.row.engId)">删除</el-button>
        </template>
      </el-table-column>
    </el-table>
    <el-pagination
      @size-change="sizeChangeHandle"
      @current-change="currentChangeHandle"
      :current-page="pageIndex"
      :page-sizes="[10, 20, 50, 100]"
      :page-size="pageSize"
      :total="totalPage"
      layout="total, sizes, prev, pager, next, jumper">
    </el-pagination>
    <!-- 弹窗, 新增 / 修改 -->
    <add-or-update v-if="addOrUpdateVisible" ref="addOrUpdate" @refreshDataList="getDataList"></add-or-update>
  </div>
</template>

<script>
  import AddOrUpdate from './engineerinformation-add-or-update'
  export default {
    data () {
      return {
        dataForm: {
          key: ''
        },
        dataList: [],
        pageIndex: 1,
        pageSize: 10,
        totalPage: 0,
        dataListLoading: false,
        dataListSelections: [],
        addOrUpdateVisible: false
      }
    },
    components: {
      AddOrUpdate
    },
    activated () {
      this.getDataList()
    },
    methods: {
      // 获取数据列表
      getDataList () {
        this.dataListLoading = true
        this.$http({
          url: this.$http.adornUrl('/generator/engineerinformation/list'),
          method: 'get',
          params: this.$http.adornParams({
            'page': this.pageIndex,
            'limit': this.pageSize,
            'key': this.dataForm.key
          })
        }).then(({data}) => {
          if (data && data.code === 0) {
            this.dataList = data.page.list
            this.totalPage = data.page.totalCount
          } else {
            this.dataList = []
            this.totalPage = 0
          }
          this.dataListLoading = false
        })
      },
      // 每页数
      sizeChangeHandle (val) {
        this.pageSize = val
        this.pageIndex = 1
        this.getDataList()
      },
      // 当前页
      currentChangeHandle (val) {
        this.pageIndex = val
        this.getDataList()
      },
      // 多选
      selectionChangeHandle (val) {
        this.dataListSelections = val
      },
      // 新增 / 修改
      addOrUpdateHandle (id) {
        this.addOrUpdateVisible = true
        this.$nextTick(() => {
          this.$refs.addOrUpdate.init(id)
        })
      },
      // 删除
      deleteHandle (id) {
        var ids = id ? [id] : this.dataListSelections.map(item => {
          return item.engId
        })
        this.$confirm(`确定对[id=${ids.join(',')}]进行[${id ? '删除' : '批量删除'}]操作?`, '提示', {
          confirmButtonText: '确定',
          cancelButtonText: '取消',
          type: 'warning'
        }).then(() => {
          this.$http({
            url: this.$http.adornUrl('/generator/engineerinformation/delete'),
            method: 'post',
            data: this.$http.adornData(ids, false)
          }).then(({data}) => {
            if (data && data.code === 0) {
              this.$message({
                message: '操作成功',
                type: 'success',
                duration: 1500,
                onClose: () => {
                  this.getDataList()
                }
              })
            } else {
              this.$message.error(data.msg)
            }
          })
        })
      }
    }
  }
</script>
