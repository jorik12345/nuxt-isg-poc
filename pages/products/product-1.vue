<template>
  <nav>
    <ul>
      <li><NuxtLink to="/">Home</NuxtLink></li>
      <li><NuxtLink to="/products/product-1">Product 1</NuxtLink></li>
      <li><NuxtLink to="/blog/blog-1">Blog 1</NuxtLink></li>
    </ul>
  </nav>
  <div v-if="pending">LOADING</div>

  <div v-else-if="error">
    {{ error }}
  </div>

  <div v-else>
    <h1>{{ data[0].title?.rendered }}</h1>
    <div v-html="data[0].content?.rendered"></div>
  </div>
</template>

<script setup>
const { data, pending, error, refresh } = await useAsyncData("product", () =>
  $fetch(
    "https://wordpress.sbaccept.nl/nl/wp-json/wp/v2/do_products/?slug=saxenda"
  )
);
</script>

<style lang="scss"></style>
