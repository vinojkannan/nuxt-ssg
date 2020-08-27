<template>
  <div>
    <h1 style="text-align: center">Nuxt SSG - Jokes</h1>
    <ul>
      <template v-for="(category, index) in categories">
        <hr :key="index" />
        <li :key="index">
          <NuxtLink :to="{ path: `jokes/${category}` }">
            {{ category }}
          </NuxtLink>
        </li>
      </template>
    </ul>
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

<style scoped>
ul {
  padding: 100px;
  list-style-type: none;
}
li {
  padding: 20px;
  text-align: center;
}
</style>
