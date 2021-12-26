<template>
  <div id="dashboard">
<ul class="collection with-header">
<li class="collection-header">
    <h4>Employee</h4>


</li>
<li v-for="employee in employees" v-bind:key="employee.id" class="collection-iteam">
   <div class="chip">  {{employee.employee_id}}</div> {{employee.name}} : {{employee.dept}}

<router-link class="secondry-content" v-bind:to="{name:'view-employee',parms:{employee_id:employee.employee_id}}">
    <i class="fa fa-eye"></i>
</router-link>
</li>
</ul>
    
    <div class="fixed-action-btn down"></div>
    <router-link to="/new" class="btn-floating 
    btn-large red">
    <i class="fa fa-plus"></i>

    </router-link>
  </div>
  
</template>

<script>
  
import db from './firebaseInit.js'
import { initializeApp } from 'firebase/app'

import {collection, getFirestore,getDocs,getDoc} from 'firebase/firestore'
const firebaseApp=initializeApp(db)
const dbs=getFirestore();

const colRef=collection(dbs,'Employee');


//console.log(db.collection('Employee'));
export default {
  name: "dashboard",
  data() {
    return {
        employees:[]
    };
  },
  created(){
      
getDocs(colRef).then(
    (snapshot)=>{

snapshot.docs.forEach(
    (doc)=>{
//this.employees.push({...doc.data()})

const data={
'id':doc.id,
'employee_id':doc.data().Employee_Id,
'name':doc.data().name,
'dept':doc.data().dept,
'position':doc.data().position


}
this.employees.push(data);
    })

console.log(this.employees);

    }


).catch(
(err)=>{
    console.log(err.message)
})

 

  },


};


</script>
