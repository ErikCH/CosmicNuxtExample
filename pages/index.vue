<template>
  <div class="container">
    <div v-if="getObjects">
      <h1 class="title text-5xl">nuxt-full-static</h1>
      <div v-for="obj in getObjects.objects" :key="obj.title">
        <div class="border-solid my-10 p-10 bg-green-200">
          <nuxt-link :to="'/blog/'+obj.slug">
            <div class="text-6xl">{{ obj.title }}</div>
          </nuxt-link>
          <!-- <div v-html="obj.content"></div> -->
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import getObjects from "~/queries/getObjects";
export default {
  apollo: {
    getObjects: {
      prefetch: true,
      query: getObjects,
    },
  },
};
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
</style>
