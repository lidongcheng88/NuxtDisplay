<template>
  <div>
    <el-container>
      <!-- Header -->
      <el-header>
        <nuxt-link to="/" style="color:#fff">
          武侠英雄榜
        </nuxt-link>
      </el-header>
      <el-container>
        <!-- Aside -->
        <el-aside width="300px">
          <el-menu
            :default-openeds="['3']"
            :default-active="$route.path"
            router
          >
            <el-submenu index="3">
              <template slot="title">
                <div style="font-weight:bold; font-size:15px">
                  武侠小说
                </div>
              </template>
              <el-menu-item v-for="(name, idx) in bname" :key="idx" :index="bookUrl(idx)">
                {{ name.bname[0] }}
              </el-menu-item>
            </el-submenu>
          </el-menu>
        </el-aside>
        <!-- Main -->
        <el-main><nuxt /></el-main>
      </el-container>
    </el-container>
  </div>
</template>

<style>
.el-header {
  background-color: #409EFF;
  line-height: 60px;
  text-align: center;
  font-size: 16px;
  font-weight:bold
}

.el-aside {
  color: #333;
  text-align: center
}

</style>

<script>
import global from '~/components/common'

export default {
  data () {
    return {
      bname: ''
    }
  },
  mounted () {
    this.$axios.get(global.prefix + '/books').then((res) => {
      console.log(res.data)
      this.bname = res.data
    })
  },
  methods: {
    bookUrl (idx) {
      const id = parseInt(idx) + 1
      return '/book/' + id
    }
  }
}
</script>
