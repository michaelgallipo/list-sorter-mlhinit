<template>
  <div id="app">
    <img id="logo" alt="Init Logo" src="./assets/MLH-Init-Logo.png">
    <h2 style="margin-top: 15px">List Sorting App</h2>
    <div id="list">
      <ul v-for="item in list" :key="item">
        <li> {{item}} </li>
      </ul>
      <div class="col-sm-6">
        <input
          type="text"
          class="form-control"
          v-model="newItem"
          maxlength="50"
          placeholder="New List Item"
          style="margin-left: 20px"
        />
      </div>
      <div id="buttons" class="row">
        <button id="addItem" class="btn btn-primary col-sm-2" v-on:click="addItem()">Add New Item</button>
        <button id="sortAZ" class="btn btn-success col-sm-2" v-on:click="sortAtoZ">Sort A-Z</button>
        <button id="sortZA" class="btn btn-warning col-sm-2" v-on:click="sortZtoA">Sort Z-A</button>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'app',

  data: function() {
    return {
      list: ["Make Bed", "Wash Dishes", "Food Shooping", "Cook Dinner", "Create MLH Init Project"],
      sortMethod: "none",
      newItem: ""
    }
  },
  methods: {
    addItem: function() {
      this.list.push(this.newItem);
      if (this.sortMethod !== "") {
        this.list.sort();
      }
      if (this.sortMethod == "Dsc") {
        this.list.reverse();
      }
      this.newItem = ""
    },
    sortAtoZ: function() {
      // console.log("function ran");
      this.list.sort();
      this.sortMethod = "Asc";
    },
    sortZtoA: function() {
      this.list.sort();
      this.list.reverse();
      this.sortMethod = "Dsc";
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
  margin-top: 30px;
}

#logo {
  height: 200px;
  width: 200px;
}

#list {
  text-align: left;
  margin-top: 20px;
}

#buttons {
  margin-top: 15px
}

#addItem {
  margin-left: 20px;
}

#sortAZ {
  margin-left: 15px;
}

#sortZA {
  margin-left: 15px;
}


</style>
