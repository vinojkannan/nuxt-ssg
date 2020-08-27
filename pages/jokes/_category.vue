<template>
  <div>
    <h1 style="padding: 100px">{{ joke.value }}</h1>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData({ $content, params }) {
    // const doc = await $content('hello').fetch()
    // return { doc }
    const { data } = await axios.get(
      `https://api.chucknorris.io/jokes/random?category=${params.category}`
    )
    return { joke: data }
  },
}
</script>
