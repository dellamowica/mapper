<template>
  <div class="container">
    <div>
      <logo />
      <h1 class="title">
        mapperfront
      </h1>
      <h2 class="subtitle">
        An online squared based map editor
      </h2>
      <div>
        {{ title }}
      </div>
      <div class="links">
        <a href="https://nuxtjs.org/" target="_blank" class="button--green">
          Documentation
        </a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          class="button--grey"
        >
          GitHub
        </a>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios"
import Logo from '~/components/Logo.vue'

export default {
  components: {
    Logo
  },
  async asyncData({ params }) {
    const { data } = await axios.get('http://mapper.docker.localhost/api')

    return {
      title: data
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
