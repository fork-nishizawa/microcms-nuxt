<template lang="pug">
  v-row(justify="center" align="center")
    v-col(cols="12" sm="8" md="10")
      ul
        li(v-for="content in contents" :key="content.id")
          nuxt-link(:to="`/${content.id}`")
            | {{ content.title}}
</template>

<script lang="ts">
import { Context } from '@nuxt/types'
import axios from 'axios'

export default {
  async asyncData({ $config }: Context) {
    const { data } = await axios.get(`${$config.apiUrl}/blog`, {
      headers: { 'X-API-KEY': $config.apiKey },
    })
    return data
  },
}
</script>
