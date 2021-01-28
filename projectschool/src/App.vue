<template>
  <div id="app">
    <Alunos/>
  </div>
</template>

<script>
import Alunos from './components/Aluno/Alunos.vue'

export default {
  name: 'App',
  components: {
      Alunos
  }
}
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Montserrat:400,700");

body{
  background-color: #eee;
  font-family: "Montserrat", sans-serif;
  display: grid;
  justify-items: center;
}
body, html {
  margin: 0;
  height: 100%;
}
#app {

}

.btn_Danger{
    background: rgb(255, 0, 0);
    color: #fff;
}

.btn{
  padding: 10px 20px;
  cursor: pointer;
  border: 1px solid #000;
  font-weight: bold;
  border-radius: 5px;
  border-bottom: 3px solid black;
}

.btn:hover{
  text-shadow: 1px 1px 1px #000;
  margin-top: 3px;
  border-bottom: 1px solid #000;
}

table {
  margin: 0px;
  padding: 0px;
  list-style-type: none;
  width: 100%;
}
table tr td{
  padding: 20px;
  font-size: 1.3em;
  background-color: rgb(28, 74, 120);
  margin-bottom: 2px;
  color: #ffffff;
}
table thead th{
  background-color: rgb(26, 114, 201) !important;
  font-size: 1.2em;
  padding: 10px 0px;
  text-align: center !important;
}
.colPequeno {
  width: 5%;
}
</style>
