<template lang="pug">
  v-row(justify="center" align="center")
    v-col(cols="12" sm="8" md="6")
      v-title
        | {{ title }}
      .post(v-html="body")
</template>

<script lang="ts">
import { Context } from '@nuxt/types'
import axios from 'axios'

export default {
  async asyncData(context: Context) {
    const { data } = await axios.get(
      `https://fork-yoh.microcms.io/api/v1/blog/${context.params.slug}`,
      {
        headers: { 'X-API-KEY': context.$config.apiKey }
      }
    )
    return data
  }
}
</script>
