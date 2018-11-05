<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <div>
      {{ stuffWeWantToShow }}
    </div>
    <div v-for="(response, index) in responses" :key="index">
      {{response.body.title}}
    </div>
  </div>
</template>

<script>

export default {
  name: 'app',
  data: () => ({
    stuffWeWantToShow: 'nothing brah',
    endpoints: [
      'https://jsonplaceholder.typicode.com/todos/1',
      'https://jsonplaceholder.typicode.com/todos/2',
      'https://jsonplaceholder.typicode.com/todos/3',
      'https://jsonplaceholder.typicode.com/todos/4'
    ],
    responses: []
  }),
  created: async function created() {
    for (const endpoint of this.endpoints) {
      try {
        const response = await this.$http.get(endpoint)
        this.responses.push(response)
        console.log(response)
      } catch (err) {
        console.log(err)
      }
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
