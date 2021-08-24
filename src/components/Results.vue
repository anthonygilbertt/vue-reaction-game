<template>
  <div class="">
    <h3>Score: {{this.reactionTime}}</h3>
  </div>
</template>

<script>
export default {
  name: 'Results',
  props: ['reactionTime']
}
</script>


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
