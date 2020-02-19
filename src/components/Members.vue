<template>
  <div id="app" class="container jumbotron">
      <table class="table">
  <thead class="thead-dark">
    <tr>
      <th scope="col">#</th>
      <th scope="col">Name</th>
      <th scope="col">Balance</th>
      <th scope="col">Action</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">1</th>
      <td>Nency</td>
      <td>${{balance1}}</td>
      <td><b-button v-b-modal.modal-1>Add Balance</b-button></td>
        <b-modal id="modal-1" ref="model1" title="Add Balance" @ok="handleSubmit1()">
          Amount : <input class="my-4" v-model.number="add1" type="number">
        </b-modal>
    </tr>
    <tr>
      <th scope="row">2</th>
      <td>Minaxi</td>
      <td>${{balance2}}</td>
      <td><b-button v-b-modal.modal-2>Add Balance</b-button></td>
        <b-modal id="modal-2" ref="model2" title="Add Balance" @ok="handleSubmit2()">
          Amount : <input class="my-4" v-model.number="add2" type="number">
        </b-modal>
    </tr>
    <tr>
      <th scope="row">3</th>
      <td>Sagar</td>
      <td>${{balance3}}</td>
      <td><b-button v-b-modal.modal-3>Add Balance</b-button></td>
        <b-modal id="modal-3" ref="model3" title="Add Balance" @ok="handleSubmit3()">
          Amount : <input class="my-4" v-model.number="add3" type="number">
        </b-modal>
    </tr>
  </tbody>
</table>
  </div>
</template>

<script>
export default {
    data() {  
      return {
        balance1:0,
        balance2:0,
        balance3:0,
        add1:0,
        add2:0,
        add3:0
      }
    },

    methods:{
      handleSubmit1(){
          this.balance1 += this.add1
      },
      handleSubmit2(){
          this.balance2 += this.add2
      },
      handleSubmit3(){
          this.balance3 += this.add3
      },
    }
}
</script>

<style>

</style>