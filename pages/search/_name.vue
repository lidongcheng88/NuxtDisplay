<template>
  <!-- <div v-html="data">
    {{ data }}
  </div> -->
  <iframe :src="baikeUrl" frameborder="0" style="width:100%; min-height:600px" />
</template>

<script>
export default {
  data () {
    // console.log(this.$route.params.name)
    const name = encodeURI(this.$route.params.name)
    const baikeUrl = 'https://baike.baidu.com/item/' + name
    return { baikeUrl }
  }
}
</script>
