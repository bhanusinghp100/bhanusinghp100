<template>
  <div id="view-employee">
    <h3>View Employee</h3>
  </div>
</template>

<script>
import db from './firebaseInit.js'
import { initializeApp } from 'firebase/app'

import {collection, getFirestore,getDocs,getDoc, QuerySnapshot} from 'firebase/firestore'
const firebaseApp=initializeApp(db)
const dbs=getFirestore();



export default {
  name: "view-employee",
  data() {
      return{
    employee_id:null,
    name:null,
    dept:null,
    position:null
     };
  },

beforeRouterEnter(to,from,next){
const colRef=collection(dbs,'Employee').where('employee_id','==',to.parms.employee_id)
.then(QuerySnapshot =>{
QuerySnapshot.forEach(element => {
    
});

});



}

};
</script>
