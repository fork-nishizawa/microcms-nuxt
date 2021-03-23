<template lang="pug">
  v-row(justify="center" align="center")
    v-col(cols="12" sm="8" md="6")
      ul
        li(v-for="content in contents" :key="content.id")
          nuxt-link(:to="`/${content.id}`")
            | {{ content.title}}
</template>

<script lang="ts">
import { Context } from '@nuxt/types'
import Logo from '~/components/Logo.vue'
import VuetifyLogo from '~/components/VuetifyLogo.vue'
import axios from 'axios'

export default {
  components: {
    Logo,
    VuetifyLogo,
  },
  async asyncData(context: Context) {
    const { data } = await axios.get(
      'https://fork-yoh.microcms.io/api/v1/blog',
      {
        headers: { 'X-API-KEY': context.$config.apiKey }
      }
    )
    return data
  },
}
</script>
