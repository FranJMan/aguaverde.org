<template>
  <InfoLayout>
    <div class="post mb" v-html="$page.info.content"></div>
  </InfoLayout>
</template>

<page-query>
query InfoPage ($path: String!) {
  info: infoPage (path: $path) {
    path
    content
    title: headings (depth: h1) {
      value
    }
  }
}
</page-query>

<script>
export default {
  metaInfo () {
    const { title } = this.$page.info

    return {
      title: title.length ? title[0].value : undefined
    }
  }
}
</script>
