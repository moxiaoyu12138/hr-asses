<template>
  <div class="dashboard-container">
    <div class="app-container">
      <!-- 组织架构头部 -->
      <el-card class="tree-card">
        <tree-tools :tree-node="company" :is-root="true" />
        <!-- 放置树状结构 -->
        <el-tree :data="departs" :props="defaultProps" :default-expand-all="true">
          <tree-tools slot-scope="{ data }" :tree-node="data" />
        </el-tree>
      </el-card>
    </div>
  </div>
</template>

<script>

import treeTools from './components/tree-tools.vue'
import { getDepartments } from '@/api/depatments'
import { tranListToTreeData } from '@/utils'
export default {
  components: {
    treeTools
  },
  data() {
    return {
      departs: [],
      defaultProps: {
        label: 'name'
      },
      company: { name: '', manager: '' }
    }
  },
  created() {
    this.getDepartments()
  },
  methods: {
    async getDepartments() {
      const result = await getDepartments()
      console.log(result)

      this.company = { name: result.companyName, manager: result.companyManage || '小雨' }
      this.departs = tranListToTreeData(result.depts, '')
    }

  }
}
</script>

<style scoped>
.tree-card{
  padding: 30px  140px;
  font-size:14px;
}

</style>
