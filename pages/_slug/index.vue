<template>
  <main class="main">
    <h1 class="title">
      {{ title }}
    </h1>
    <p class="publishedAt">
      {{ publishedAt }}
    </p>
    <div class="post" v-html="body" />
  </main>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData ({ params }) {
    const { data } = await axios.get(
      `https://frontdevmiya.microcms.io/api/v1/blog/${params.slug}`,
      {
        headers: { 'X-API-KEY': 'ca4688c1-02b1-4f17-8c32-53aa1c198fe7' }
      }
    )
    return data
  }
}
</script>
