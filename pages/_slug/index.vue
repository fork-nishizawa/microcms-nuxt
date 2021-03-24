<template lang="pug">
  v-row(justify="center" align="center")
    v-col(cols="12" sm="8" md="10")
      v-title
        | {{ title }}
      .post(v-html="body")
</template>

<script lang="ts">
import { Context } from '@nuxt/types'
import axios from 'axios'

export default {
  async asyncData({ $config, params }: Context) {
    const { data } = await axios.get(`${$config.apiUrl}/blog/${params.slug}`, {
      headers: { 'X-API-KEY': $config.apiKey },
    })
    return data
  },
}
</script>
