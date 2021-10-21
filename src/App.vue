<template>
  <div class="text-center">
    <div v-for="airline in airlines" v-bind:key="airline.id">
      <h2>{{ airline.name }}</h2>
      <img class="w-100 rounded-full" v-bind:src="airline.logo" />
    </div>
    <h1>fun</h1>
  </div>
</template>

<script>

export default {
  data() {
    return {
      airlines: [],
    };
  },

  methods: {
    async getData() {
      try {
        const response = await this.$http.get(
            "http://localhost/api/airlines"
        );
        this.airlines = response.data
      } catch (error) {
        console.log(error);
      }
    },

  },

  created() {
    this.getData();
  }
};
</script>

<style>

</style>
