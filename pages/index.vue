<template>
  <div>
    <h1 style="text-align: center">VUE SSG - Jokes</h1>
    <v-container>
      <v-list three-line>
        <template v-for="(category, index) in categories">
          <v-divider :key="index"></v-divider>
          <v-list-item :key="category">
            <v-list-item-content>
              <v-list-item-title>
                <NuxtLink :to="{ path: `jokes/${category}` }">
                  {{ category }}
                </NuxtLink>
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </template>
      </v-list>
    </v-container>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData({ $content, params }) {
    // const doc = await $content('hello').fetch()
    // return { doc }
    const { data } = await axios.get(
      'https://api.chucknorris.io/jokes/categories'
    )
    return { categories: data }
  },
}
</script>
