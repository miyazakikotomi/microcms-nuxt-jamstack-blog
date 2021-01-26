<template>
  <div>
    今日も寒いです。
    <ul>
      <li v-for="content in contents" :key="content.id">
        <nuxt-link :to="`/${content.id}`">
          {{ content.title }}
        </nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  async asyncData () {
    const { data } = await axios.get(
      // your-service-id部分は自分のサービスidに置き換えてください
      'https://frontdevmiya.microcms.io/api/v1/blog',
      {
        // your-api-key部分は自分のapi-keyに置き換えてください
        headers: { 'X-API-KEY': 'ca4688c1-02b1-4f17-8c32-53aa1c198fe7' }
      }
    )
    return data
  }
}
</script>
