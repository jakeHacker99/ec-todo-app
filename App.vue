<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" width="120px" />
    <div class="contain">
      <h1  >TEFLON</h1>
      <p style="font-size: 0.6rem">När det inte fastnar</p>

      <h3 >Du har {{ existingTodo.length }} todos kvar att göra</h3>

      <ul class="center" style="margin-right: 25%;">
        <li  v-for="(todo, i) in existingTodo" v-bind:key="i" class="center" id="right-me">
          <span >
            <input type="checkbox" checked="checked" class="box">
            {{ todo.text }}
          </span>

          <button class="delete-button" @click="deleteTodo(i)">x</button>
        </li>
      </ul>
        <input id="input-2" v-model="newTodo" />
        <div class="">
          <button class="add-button" id="btn-add" v-on:click="add()">
            Lägg till
          </button>
        </div>

    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      newTodo: "",
      existingTodo: 
        [{ text: "Bananer", id: 0 },
       { text: "Kaffe", id: 1 }, 
       { text: "Keso", id: 2 }, 
       { text: "Roliga keps med djurmotiv", id: 3 }]
    };
  },
  methods: {
    add() {
      this.existingTodo.push({
        text: this.newTodo,
        id: new Date().valueOf(),
      }),
        (this.newTodo = "");
    },

    deleteTodo(i) {
      this.existingTodo.splice(i, 1);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#btn-add {
  background: #000;
  color: white;
  width: 25.1%;
  margin-top: 0.2%;
}

li{
  background: #d0d0d0;
  width: 40%;
  margin-right: 130px;
  height: 60px;
}



.center {
    display: block;
    margin-left: auto;
    margin-right: auto;
    width: 50%;
  }


.delete-button{
    cursor: pointer;
    margin: auto;
    font-size: .6rem;

}
  


#input-2{
  width: 24.3%;
}

.box{
  margin: auto;
  float: left;
  margin-top: 2%;
}
</style>
