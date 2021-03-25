<template>
<div>
  <h1>STAR WARS CHARACTERS</h1>
  <ul>
    {{people}}
  </ul>
</div>
</template>

<script>
export default {
  data: function () {
    return {
      people: {

      },

      mounted:function () {
        this.getPeople()
      },
      methods: {
        getPeople: function () {
          this.$http.get("https://swapi.dev/api/people/1")
              .then(res => {
                this.people= res.body

              });

        },
      }
    }
  }
}
</script>

<style scoped>

</style>