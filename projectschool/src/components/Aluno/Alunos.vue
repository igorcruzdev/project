<template>
  <div>
    <div class="title"><Titulo texto="Cadastro de alunos"/></div>
    <div>
      <input type="text" placeholder="Nome do Aluno" v-model="nome"
      @keyup.enter="addAluno()">
      <button class="btn btnInput" @click="addAluno()">Cadastrar</button>
    </div>
  
    <table>
      <thead>
        <th>Matricula</th>
        <th>Nome</th>
        <th>Opcoes</th>
      </thead>
      <tbody v-if="alunos.length">
        <tr v-for="(aluno, index) in alunos" :key="index">
          <!-- <td>{{index+1}}</td> -->
          <td>{{aluno.id}}</td>
          <td>{{aluno.nome}} {{aluno.sobrenome}}</td>

          <td>
            <button class="btn btn_Danger" @click="remover(aluno)">Remover</button>
          </td>
        </tr>
      </tbody>
      <tfoot v-if="!alunos.length"> <br>
        Nenhum Aluno Encontrado
      </tfoot>
    </table>
  </div>
</template>

<script>
import Titulo from '../_share/Titulo'

export default {
  components: {
    Titulo
  },
  data() {
    return {
      titulo: "Cadastro de alunos",
      nome: "",
      alunos: []
        }
    },
    created() {
      this.$http.get('http://localhost:3000/alunos')
      .then(res => res.json())
      .then(alunos => this.alunos = alunos)
    },
    props: {

    },
    methods: {
      addAluno(){
        let _aluno = {
          nome: this.nome,
          sobrenome: "",
        }

        this.$http.post('http://localhost:3000/alunos', _aluno)
          .then(res => res.json())
          .then(alunoRetornado => {
            this.alunos.push(alunoRetornado)
            this.nome = ''
          })

        //this.alunos.push(_aluno);
        // console.log("-----")
        // this.alunos.forEach(aluno => {
        //   console.log(aluno)
        // })
        //this.nome = '';
      },
      remover(aluno) {
        this.$http.delete(`http://localhost:3000/alunos/${aluno.id}`)
          .then(() => {
            let indice = this.alunos.indexOf(aluno);
            this.alunos.splice(indice, 1);
          })
      }
    },
  }
</script>


<style scoped>
input{
  border: 0;
  padding: 20px;
  font-size: 1.3em;
  color: #687f7f;
  display: inline;
}
.btnInput{
  border: 0px;
  width: 150px;
  padding: 20px;
  font-size: 1.3em;
  display: inline;
  background-color: rgb(116, 115, 115);
}
.btnInput:hover{
  padding: 20px;
  margin: 0px;
  border: 0px;
}
.title{
  border: 5px groove #000;
  text-align: center;
  margin-bottom: 10px;
  margin-top: 10px;
}
</style>
