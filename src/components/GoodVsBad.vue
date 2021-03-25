<template>
    <div>
      <h1>DBZ Characters</h1>

        <ul name="Characters" size="5">
          <option> {{}} </option>
        </ul>

      <button type="button" v-on:click="addCharacters()">add Character</button>

      <ul name="goodCharacters" size="5">
        <option> {{charactersV3[0].good}} </option>
      </ul>


        <ul name="Badcharacters" size="5" placeholder="good">
          <option> {{charactersV3[1].bad}} </option>
        </ul>

    </div>
</template>

<script>
export default {
  data: function() {
    return {
      printedCharacter :{
        name:[]
      },
      character: {name:"Gohan", place:"earth", age:"22"},
      character2: {name:"vegeta", place:"earth", age:"40"},

      charactersV3: [
        {"good": [
            {name: "Goku", place: "earth", age: "28"},{name: "Krillin", place: "earth", age: "26"}]},
        {"bad": [
            {name: "Cell", place: "earth", age: "28"},{name: "Buu", place: "earth", age: "26"}]}]
    };
  },
  mounted: function() {
    this.getNames()
    this.getBadNames()
  },
  methods: {
    getNames: function () {
      for (let i = 0; i < this.charactersV3.length; i++) {
        if(this.charactersV3[i].good != undefined && this.charactersV3[i].good != null) {
          for (let j=0;j<this.charactersV3[i].good.length;j++) {
            console.log("good: " + this.charactersV3[i].good[j].name)
            this.printedCharacter.name.push(this.charactersV3[i].good[j].name)
          }
        }
      }
    },
    getBadNames: function () {
      for (let i = 0; i < this.charactersV3.length; i++) {
        if(this.charactersV3[i].bad != undefined && this.charactersV3[i].bad != null) {
          for (let j=0;j<this.charactersV3[i].bad.length;j++) {
            console.log("bad: " + this.charactersV3[i].bad[j].name)
            this.printedCharacter.name.push(this.charactersV3[i].bad[j].name)
          }
        }
      }
    },
    addCharacters: function () {
      this.charactersV3[0].good.push(this.character)
    },
    addBadCharacters: function () {
      this.charactersV3.bad.push(this.character)
    },
    removeGoodCharacter:function () {
      this.charactersV3.good.splice(1,1)
    },
    removeBadCharacter:function () {
      this.charactersV3.bad.splice(1,1)
    }
  }
};
</script>

<style scoped>

</style>