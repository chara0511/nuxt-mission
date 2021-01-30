<template>
  <div class="container">
    <div>
      <img :src="planet.image" class="rounded" />
      <h1 class="title">{{ planet.title }}</h1>
      <p>{{ planet.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  transition: 'bounce',
  async asyncData({ params }) {
    const planet = await fetch(
      `https://api.nuxtjs.dev/planets/${params.slug}`
    ).then((res) => res.json())

    return { planet }
  },
  head() {
    return {
      title: this.planet.title,
      htmlAttrs: {
        lang: 'en',
      },
      meta: [
        { charset: 'utf-8' },
        { name: 'viewport', content: 'width=device-width, initial-scale=1' },
        {
          hid: 'description',
          name: 'description',
          content: this.planet.description,
        },
      ],
      link: [
        {
          hid: 'canonical',
          rel: 'canonical',
          href: `https://jamstack-explorers-nuxt-mission/${this.$route.params.slug}`,
        },
        { rel: 'icon', type: 'image/x-icon', href: '/favicon.ico' },
      ],
    }
  },
}
</script>

<style scoped>
.title {
  font-family: Nunito, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.rounded {
  height: 120px;
  width: auto;
  object-fit: cover;
  border-radius: 50%;
}
</style>
