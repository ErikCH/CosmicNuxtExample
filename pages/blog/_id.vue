<template>
  <div v-if="page">
    <div v-html="page"></div>
  </div>
</template>

<script>
import getObject from "~/queries/getBlog";
export default {
  async asyncData({ app, route, redirect }) {
    let data = {};
    try {
      const d = await app.apolloProvider.defaultClient.query({
        query: getObject,
        variables: { slug: route.params.id },
      });
      const data = d.data;
      console.log("data", data);
      return {
        page: data.getObject.content,
      };
    } catch (error) {
      console.log("error", error);
      redirect("/");
    }
  },
  mounted() {
    console.log(this.myRoute);
  },
  computed: {
    myRoute() {
      return this.$route.params.id;
    },
  },
};
</script>

<style lang="scss" scoped>
</style>