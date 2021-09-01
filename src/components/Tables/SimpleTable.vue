<template>

  <div>

    <md-table v-model="users" :table-header-color="tableHeaderColor">
      <md-table-row slot="md-table-row" slot-scope="{ item }">
        <md-table-cell md-label="Name">{{ item.name }}</md-table-cell>
        <md-table-cell md-label="Country">{{ item.country }}</md-table-cell>
        <md-table-cell md-label="City">{{ item.city }}</md-table-cell>
        <md-table-cell md-label="Salary">{{ item.salary }}</md-table-cell>
      </md-table-row>
    </md-table>

<button @click="addContact">연락처 1건 추가</button>
<button @click="fetchContacts">목록 추가</button>
        <p>안녕</p>
    <p>{{result}}</p>

    <md-table v-model="todos" :table-header-color="tableHeaderColor">
      <md-table-row slot="md-table-row" slot-scope="{ item }">
        <md-table-cell md-label="Name">{{ item.userId }}</md-table-cell>
        <md-table-cell md-label="Country">{{ item.id }}</md-table-cell>
        <md-table-cell md-label="City">{{ item.title }}</md-table-cell>
        <md-table-cell md-label="Salary">{{ item.body }}</md-table-cell>
      </md-table-row>
    </md-table>

  </div>
</template>

<script>
import { onMounted, reactive } from 'vue';
import axios from 'axios';

export default {
  name: "simple-table",
   methods : {
        fetchContacts : function() {

            axios({
                method: 'GET',
                url : 'https://jsonplaceholder.typicode.com/posts/',
                params : {
                    page : 1,
                    pagesize : 5
                }
            }).then((response) => {
                //console.log(response);
                this.result = response.data.title;
                this.todos = response.data ;
                console.log(response.data);
                console.log(this.todos);
            }).catch((ex)=> {
                console.log("ERR!!!!! : ", ex)
            })


        },

        addContact : function() {
            axios({
                method: 'GET',
                url : 'https://jsonplaceholder.typicode.com/posts/1',
                params : {
                    page : 1,
                    pagesize : 5
                }
            }).then((response) => {
                //console.log(response);
                this.result = response.data.title;
                this.todos.push(response.data) ;
                console.log(response.data);
                console.log(this.todos);
            }).catch((ex)=> {
                console.log("ERR!!!!! : ", ex)
            })
        },

        fetchContactOne : function() {

        },

        updateContact : function() {

        },

        deleteContact : function() {

        },

        changePhoto : function() {

        }
    },
  props: {
    tableHeaderColor: {
      type: String,
      default: ""
    }
  },
  data() {
    return {
      selected: [],
      result:"test",
      todos:[
        {
          userId: "Dakota Rice",
          id: "$36,738",
          title: "Niger",
          body: "Oud-Turnhout"          
        }
      ],
      users: [
        {
          name: "Dakota Rice",
          salary: "$36,738",
          country: "Niger",
          city: "Oud-Turnhout"
        },
        {
          name: "Minerva Hooper",
          salary: "$23,738",
          country: "Curaçao",
          city: "Sinaai-Waas"
        },
        {
          name: "Sage Rodriguez",
          salary: "$56,142",
          country: "Netherlands",
          city: "Overland Park"
        },
        {
          name: "Philip Chaney",
          salary: "$38,735",
          country: "Korea, South",
          city: "Gloucester"
        },
        {
          name: "Doris Greene",
          salary: "$63,542",
          country: "Malawi",
          city: "Feldkirchen in Kārnten"
        },
        {
          name: "Mason Porter",
          salary: "$78,615",
          country: "Chile",
          city: "Gloucester"
        }
      ]
    };
  }
};
</script>
