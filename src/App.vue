<script setup>
import { ref, onMounted } from 'vue'

// reactive state
const count = ref(0)

// functions that mutate state and trigger updates
function increment() {
  count.value++
}

// lifecycle hooks
onMounted(() => {
  console.log(`The initial count is ${count.value}.`)
})
const text = ref('Athan'); 
const newText = ref(''); 

const selector = ref('');
const color = ref('');

function updateMainText() {
    text.value = newText.value;
}

function changeColor() {
    const elements = document.querySelectorAll(selector.value);
    elements.forEach(el => {
        el.style.backgroundColor = color.value; 
    });
}


</script>

<template>
 <div id="navbar" class="container">  
        <div id="title">Athan's website</div>
        <div id="logo">
            <img src="@/assets/cow.jpg" alt="macad cow">

        </div>
        

    </div>


    <button @click="increment">Count is: {{ count }}</button>

    <div id="flex">
       <div id="sidebar" class="container">
           Sidebar
           <div>
               <input type="text" v-model="selector" placeholder="#">
               <input type="text" v-model="color" placeholder="Color">
               <button @click="changeColor">Change Color</button>
           </div>
           
           <div>
               <input type="text" v-model="newText" placeholder="New Text">
               <button @click="updateMainText">Change Text</button>
           </div>
       </div>
       <div id="main" class="container">
           {{ text }}
       </div>
   </div>

</template>

<style scoped>
html{
    
    background-color: rgb(59, 59, 59); 
    color: white;
}

body{

    margin:0;
}

div{

    /* put the borders in the inside of container */
    box-sizing: border-box;
}

img{

    height: 100%;
    width: auto;

}

#navbar{

    height: 50px;
    border-color: red;


}

#flex{
    
    display: flex;
    height: calc(100vh - 50px);
}

#sidebar{
    
    width:30%;
    border-color: blue;

}

#main{
    width:70%;
    border-color: green;

}

#title{
    width: 70%;
    float:left;
}

#logo{
    width: 30%;
    height: 100%;
    float:right;
    text-align: right;

}

.container{

    border-style: dotted;
    border-width: 1px;

}
</style>