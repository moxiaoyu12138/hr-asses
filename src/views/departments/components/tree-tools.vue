<template>
  <el-row type="flex" justify="space-between" align="middle" style="height: 40px; width:100%;">
    <el-col>
      <!-- 头部左侧内容 -->
      <span>{{ treeNode.name }}</span>
    </el-col>
    <el-col :span="4">
      <el-row type="flex" justify="end">
        <el-col>{{ treeNode.manager }}</el-col>
        <el-col>
          <!-- 放置下来菜单 -->
          <el-dropdown>
            <!-- 内容 -->
            <span>操作
              <i class="el-icon-arrow-down" />
            </span>
            <!-- 下拉菜单 -->
            <el-dropdown-menu slot="dropdown">
              <!-- 具名插槽 -->
              <el-dropdown-item>添加子部门</el-dropdown-item>
              <el-dropdown-item v-if="isRoot">编辑部门</el-dropdown-item>
              <el-dropdown-item v-if="isRoot">删除部门</el-dropdown-item>
            </el-dropdown-menu>
          </el-dropdown>
        </el-col>
      </el-row>
    </el-col>
  </el-row>
</template>

<script>
export default {
  props: {
    treeNode: {
      required: true,
      type: Object
    },
    isRoot: {
      required: false,
      type: Boolean
    }
  }
}
</script>

<style>

</style>
