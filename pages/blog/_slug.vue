<template>
  <div class="container">

    


    {{ story.content }}
    <div>
      <logo />
      <nuxt-link to="/">Home page</nuxt-link>
      <nuxt-link to="/about">About</nuxt-link>
      <nuxt-link to="/blog/1">First blog</nuxt-link>
      <nuxt-link to="/blog/2">Second blog</nuxt-link>
      <h1 class="title">
        moirawest2019
      </h1>
      <h2 class="subtitle">
        Moira West Marketing Website
      </h2>
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
import Logo from '~/components/Logo.vue'

export default {
  components: {
    Logo
  },
  data () {
    return {
       story: { content: {} },
       links: {},
       stories: {}
    }
  },
  methods: {
    blogLink(story) {
      return `blog/${story.slug}`
    }
  },
  asyncData (context) {
      console.dir(context.app)
    return context.app.$storyapi.get('cdn/stories/blog/' + context.params.slug)
      .then((res) => {
      return res.data
    })
  }
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
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
