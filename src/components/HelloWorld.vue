<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>{{ lambdaMsg }}</p>
    <button @click="callLambda">Click here</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      lambdaMsg: "Click to call a lambda"
    }
  },
  methods: {
    callLambda() {
      fetch("/.netlify/functions/hello").then(response => response.json()).then((json) => {
        this.lambdaMsg = json.msg
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
