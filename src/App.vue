<template>
  <div id="app">
    <h1 class="title">LKMX - Front-end</h1>

    <div class="app1">
      <h1 class="title_second">To Do List</h1>

      <div class="div_input_btn">
        
          <input
            class="input_add"
            focusable
            type="text"
            v-model="name"
            id="name"
            v-on:keyup.enter="addTask"
            placeholder="Escribe una tarea"
          />

          <button class="btn_add" @click="addTask">Agregar</button>
        
      </div>

      <div class="div_table">
        <table class="data">
          <tbody>
            <tr v-for="(item, index) of tasks"> 
              <td>
                <span v-if="formActualizar && idActualizar == index">
                  <input
                    type="text"
                    class="input_edit"
                    v-model="nameActualizar"
                  />
                </span>
                <span v-else
                  ><div class="name">+ {{ item.name }}</div></span
                >
              </td>

              <td>
                <span v-if="formActualizar && idActualizar == index">
                  <button class="btn_edit" @click="editTask(index)">
                    <img src="./assets/icon-disk.svg" />
                  </button>
                </span>
                <span v-else>
                  <button class="btn_delete" @click="deleteTask(index)">
                    <img src="./assets/icon-trash.svg" />
                  </button>
                  <button class="btn_edit" @click="verFormActualizar(index)">
                    <img src="./assets/icon-pen.svg" />
                  </button>
                </span>
              </td>   

            </tr>

         <!--   <tr v-show="vacio">
              <span>{{mensaje}}</span>
            </tr>-->
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tasks: [],
      name: "",
      condition: false,
      formActualizar: false,
      formVacio: false,
      idActualizar: -1,
      nameActualizar: "",
      mensaje: "No has agregado tareas",
    };
  },
  methods: {
    addTask() {
      this.tasks.push({
        name: this.name,
      });

      this.name = "";
    },
    editTask(index) {
      this.formActualizar = false;

      this.tasks[index].name = this.nameActualizar;
    },
    verFormActualizar(index) {
      this.idActualizar = index;
      this.nameActualizar = this.tasks[index].name;

      this.formActualizar = true;
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
    vacio() {
      this.tasks[index].name = null;
    },
  },
};
</script>


<style>
body {
  background-color: gainsboro;
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  box-sizing: border-box;
}

.title {
  margin: 10px;
  padding: 10px;
}

input:focus,
input[type]:focus {
  border-color: red;
  box-shadow: 0 0 0 rgba(229, 103, 23, 0.075) inset, 0 0 0 red;
  outline: 0 none;
}
.title_second {
  margin: 5px;
  margin-left: 0px;
  margin-bottom: 10px;
  padding: 0px;
  padding-bottom: 0px;
}

.app1 {
  background-color: white;
  margin: 20px;
  padding: 30px;
  padding-top: 5px;
  width: 50%;
  border-radius: 5px;
}

.div_input_btn {
  padding: 0px;
  margin: 0px;
}

.btn_add {
  background-color: #0275d8;
  color: white;
  border-radius: 5px;
  padding: 0px;
  margin: 0px;
  border-style: none;
  width: 20%;
  height: 40px;
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  font-size: 100%;
  float: right;
  cursor: pointer;
}

.div_table {
  padding: 0px;
  margin-top: 10px;
  text-align: center;
}
.data {
  width: 100%;
  height: 60px;
  margin: 0px;
  padding: 0px;
  border-radius: 5px;
  background-color: gainsboro;
  text-align: left;
}
.name {
  margin-left: 20px;
  text-align: left;
}

.input_add {
  width: 75%;
  height: 40px;
  border-radius: 5px;
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  font-size: 100%;
  border: 0.5px solid #ccc;
}

.input_edit {
  width: 100%;
  height: 40px;
  margin-left: 10px;
  margin-right: 0px;
  border-radius: 5px;
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  font-size: 100%;
  border: 1px solid #ccc;
  float: left;
  text-align: left;
}

td {
  margin: 0px;
  margin-top: 10px;
  padding: 0px;
}

.btn_edit {
  float: right;
  margin-right: 5px;
  padding-left: 5px;
  cursor: pointer;
}

.btn_delete {
  float: right;
  margin-right: 5px;
  cursor: pointer;
}

.vacio {
  font-size: 30px;
  margin-left: 20px;
  margin-top: 20px;
  color: gray;
}
</style>
