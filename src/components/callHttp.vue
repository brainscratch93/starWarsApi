<template>
<div>

  <li>
      {{people.name}}
  </li>
</div>

</template>

<script>
export default {
  data: function() {
    return {
      people: {
        name: "",
      },
      newName:"mirko",
      character: {name:"Gohan", place:"earth", age:"22"},
      x: 1,
      names: ["bob", "pippo", "mike"],
      animals: {dog: "fido", cat: "miao", fish: "giulio"},
      characters: [{name: "Goku", place: "earth", age: "28"}, {name: "Vegeta", place: "earth", age: "31"}],
      charactersV2: {"good": [
          {name: "Goku", place: "earth", age: "28"},{name: "Krillin", place: "earth", age: "26"}]},

      charactersV3: [
          {"good": [
          {name: "Goku", place: "earth", age: "28"},{name: "Krillin", place: "earth", age: "26"}]},
        {"bad": [
          {name: "Bulma", place: "earth", age: "28"},{name: "Kiki", place: "earth", age: "26"}]}]
    };
  },
  mounted: function() {
    this.addCharacters()
    this.getPeople()
    this.getNames()
    this.removeCharacter()

  },
  methods: {
    getPeople: function () {
      this.$http.get("https://swapi.dev/api/people/")
          .then(res => {
            this.people = res.body;
          });

    },

    getNames: function () {

      console.log(this.animals)
      console.log(this.characters)
     this.names.forEach(element => console.log(element))
      let i

      this.characters.forEach((element) => console.log(element.name))
      this.charactersV2.good.forEach((element) => console.log(element))


      for (i = 0; i < this.charactersV3.length; i++) {
        if(this.charactersV3[i].good != undefined && this.charactersV3[i].good != null) {
          for (let j=0;j<this.charactersV3[i].good.length;j++) {
            console.log("good: " + this.charactersV3[i].good[j].name)
          }
        }
      }
    },
    addCharacters: function () {
      this.names.push(this.newName)
      this.characters.push(this.character)
      this.charactersV2.good.push(this.character)
    },
    removeCharacter:function () {
      this.characters.splice(1,1)
    }
  }
};
</script>

<style scoped>

</style>