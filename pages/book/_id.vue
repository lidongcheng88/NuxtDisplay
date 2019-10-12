<template>
  <el-table
    :data="tableData"
    style="width: 100%"
  >
    <el-table-column
      prop="hname"
      label="英雄"
      min-width="100%"
      align="center"
      sortable
    >
      <template slot-scope="scope">
        <nuxt-link :to="'/search/' + scope.row.hname">
          {{ scope.row.hname }}
        </nuxt-link>
      </template>
    </el-table-column>
  </el-table>
</template>

<script>
import axios from 'axios'
import global from '~/components/common'

export default {
  validate ({ params }) {
    // 必须是number类型
    return /^\d+$/.test(params.id)
  },
  async asyncData ({ params }) {
    const resp = await axios.get(global.prefix + `/book/${params.id}`)
    // console.log(resp.data)
    return { tableData: resp.data }
  }
}
</script>
