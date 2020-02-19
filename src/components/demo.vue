<template>
  <div id="app" class="container jumbotron">
    
    <div class="overflow-auto">
      <p class="center">Number of Records : <input ref="number" v-model="perPage" placeholder="Type Number of Records"/></p>
      <br>
      <b-pagination
        v-model="currentPage"
        :total-rows="rows"
        :per-page="perPage"
        aria-controls="my-table"
      ></b-pagination>
      <br>
    <p class="mt-3" v-if="perPage == 0">Current Page: {{ currentPage }}</p>
    <p class="mt-3" v-else>Current Page: {{ currentPage }} out of {{totalPages}}</p>
    <br>
      <b-table class="table"
        id="my-table"
        :fields="fields"
        :items="items"
        :current-page="currentPage"
        :per-page="perPage">
        <!-- <thead class="thead-dark">
          <tr>
            <th scope="col">#</th>
            <th scope="col">Name</th>
            <th scope="col">Balance</th>
            <th scope="col">Action</th>
          </tr>
        </thead> -->
        <!-- <tbody>
          <tr v-for="item in items" :key="item.id">
            <th>{{item.id}}</th>
            <td>{{item.first_name}}</td>
            <td>${{item.Balance}}</td>
            <td><b-button v-b-modal="'my-modal'+item.id">Add Balance</b-button></td>
              <b-modal :id="'my-modal'+item.id" title="add balance" @ok="addBalance(item)">
                Amount : <input class="my-4" v-model.number="add" type="number">
              </b-modal>
          </tr>
        </tbody> -->
        <template v-slot:cell(action)="data">
          <b-button @click="openModal(data.item)">Add balance</b-button>
        </template>
        <!-- <b-modal :id="'my-modal'+items.id" title="add balance" @ok="addBalance(item)">
                Amount : <input class="my-4" v-model.number="add" type="number">
              </b-modal> -->
       
    </b-table>
        <b-modal ref="my-modal" @ok="addBalance">
           Amount : <input class="my-4" v-model.number="add" type="number">
        </b-modal>
              
    </div>


     
  </div>
</template>

<script>
export default {
    data() {  
      return {
        add:0,
        balance:0,
        perPage: 5,
        currentPage: 1,
        fields: ['id', 'first_name', 'Balance', 'action'],
        items :
          [
            { id:1 , first_name: 'Nency', Balance: 0 },
            { id:2 , first_name: 'Minaxi', Balance: 0 },
            { id:3 , first_name: 'Sagar', Balance: 0},
            { id:4 , first_name: 'Riya', Balance: 0 },
            { id:5 , first_name: 'Bhoomi', Balance: 0 },
            { id:6 , first_name: 'Hemangi', Balance: 0 },
            { id:7 , first_name: 'Mayuri', Balance: 0 },
            { id:8 , first_name: 'Nikita', Balance: 0 },
            { id:9 , first_name: 'Bhagi', Balance: 0 },
            { id:10 , first_name: 'Digesh', Balance: 0 },
            { id:11 , first_name: 'Ritesh', Balance: 0 },
            { id:12 , first_name: 'Khushbu', Balance: 0 },
            { id:13 , first_name: 'Nadir', Balance: 0 },
            { id:14 , first_name: 'Nirali', Balance: 0 },
            { id:15 , first_name: 'Binal', Balance: 0 },
            { id:16 , first_name: 'Chandresh', Balance: 0 },
            { id:17 , first_name: 'Avani', Balance: 0 },
            { id:18 , first_name: 'Reena', Balance: 0 },
            { id:19 , first_name: 'Vivek', Balance: 0 },
            { id:20 , first_name: 'Richa', Balance: 0 },
            { id:21 , first_name: 'Ruchi', Balance: 0 },
            { id:22 , first_name: 'Mayank', Balance: 0 },
            { id:23 , first_name: 'Aman', Balance: 0 },
            { id:24 , first_name: 'Jeet', Balance: 0 },

          ],
      }
    },

    mounted(){
      this.$refs.number.focus()
    },
     computed: {
      rows() {
        return this.items.length
      },

      totalPages: function() {
        return Math.ceil(this.items.length / this.perPage);

    }
    },
    methods:{
      openModal(item){
        this.tempdata = item
        this.$refs['my-modal'].show()
      },
      addBalance(){
        this.tempdata.Balance += this.add
        localStorage.setItem("balance",this .tempdata.Balance)
                  // item.Balance +=  this.add
                }
                  
          // this.items[id] = id
          // this.balance += this.add
      },
     
    }

</script>

<style>

</style>