<template>
  <el-table :data="tableData" stripe style="width: 100%">
    <el-table-column
      prop="hname"
      label="英雄"
      min-width="50%"
      align="center"
      sortable
    >
      <template slot-scope="scope">
        <nuxt-link :to="'/search/' + scope.row.hname">
          {{ scope.row.hname }}
        </nuxt-link>
      </template>
    </el-table-column>
    <el-table-column prop="bname" label="武侠小说" align="center" sortable>
      <template slot-scope="scope">
        <nuxt-link :to="'/search/' + scope.row.bname">
          {{ scope.row.bname }}
        </nuxt-link>
      </template>
    </el-table-column>
  </el-table>
</template>

<script>
import axios from 'axios'
import global from '~/components/common'

export default {
  async asyncData () {
    const resp = await axios.get(global.prefix)
    // console.log(resp.data)
    return { tableData: resp.data }
  }
}
</script>
