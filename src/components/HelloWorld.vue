<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h1>{{ info }}</h1>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      info: ""
    }
  },
  mounted() {
    axios.get(process.env.VUE_APP_BASE_API + "users", {
      headers: { "Authorization": "Token " + process.env.VUE_APP_API_TOKEN }
    }).then(response => (this.info = response))
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
