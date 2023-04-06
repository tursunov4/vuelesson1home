<template>
  <div>
    <h2 class="mb-2">{{ count }} metr </h2>
    <button @click="addCount" class="btn btn-info">Yurish</button>
    <hr>
    <h3 class="mb-2">Qadam kattaligi : {{ qadam }} metr</h3>
    <button class="btn mb-5 btn-success" @click="addQadam">Qadam kengaytirish</button>
   <hr>
    <div>
      <button  @click="sortarmiya" class="btn mb-5 d-block mt-4 mx-auto btn-danger"> armiyaga qabul qilish</button>
      <div class="col-md-8 mx-auto">
        <table class="table table-success">
          <thead>
            <th>id</th>
            <th>firstname</th>
            <th>lastname</th>
            <th>age</th>
            <th>dept_number</th>
            <th>City</th>
            <th>state</th>
            <th>salar</th>
          </thead>
          <tbody>
            <tr v-for="(item , index) in arr" :key="index">
              <td>{{ item.id }}</td>
              <td>{{ item.firstname }}</td>
              <td>{{ item.lastname }}</td>
              <td>{{ item.age }}</td>
              <td>{{ item.dept }}</td>
              <td>{{ item.city }}</td>
              <td>{{ item.state }}</td>
              <td>{{ item.salary }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
      <hr>
      <div>
        <button @click="addCounts" class="btn btn-info mt-4 d-block mx-auto">Add Counts</button>
        <div class="mx-5 my-2" v-for="(item , index) in countArr" :key="index" >
          <button @click="()=>countsAdd(item.id)" class="btn btn-success m-2">+</button>
          <span>{{ item.count }}</span>
          <button @click="()=>removeCounts(item.id)" class="btn btn-danger m-2">-</button>
        </div>
      </div>
  </div>
</template>

<script setup>
   import { ref } from 'vue';
   const count = ref(0)
   const qadam = ref(1)
   const addCount =() =>{
    count.value +=qadam.value
   }
   const addQadam =() =>{
    qadam.value +=1
   }
   const arr = ref([
    {id:1 , firstname:'ali' , lastname :'vali' , age : 14, dept :100, city:'tashkent' , state :'IL' , salary:1000},
    {id:2 , firstname:'vali' , lastname :'vali' , age : 19, dept :200, city:'chirchiq' , state :'IL' , salary:2000},
    {id:3 , firstname:'quzi' ,  lastname :'vali' ,age : 20, dept :300, city:'qoqon' , state :'IL' , salary:3000},
    {id:4 , firstname:'quzi oy' , lastname :'vali' , age : 15, dept :100, city:'navoi' , state :'IL' , salary:1000},
   ])
   const sortarmiya =() =>{
    arr.value = arr.value.filter((item) => item.age > 18)
   }
   const countArr = ref([])
   const addCounts =() =>{
    countArr.value.push({id:countArr.value.length , count:0})
   }
   const countsAdd =(id) =>{
    countArr.value[id].count +=1
   }
   const removeCounts =(id) =>{
    countArr.value[id].count -=1
   }
</script>

<style  scoped>
  h1{
    color: red;
  }
</style>