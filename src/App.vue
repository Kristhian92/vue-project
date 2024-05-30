<script setup>
import { ref, computed } from 'vue';
const name = "Vue";
// const styleColor = "color:blue";
const arrayColores = ["blue", "red", "peru"];
// const arrayFruits = ["🍒", "🍓", "🍌", "🍍", "🥭", "🍎"];
// const arrayFrutas = [
//   {
//     name: "Manzana",
//     price: "1.00",
//     description: "Una manzana",
//     stock:-1,
//     id: 1,
//   },
//   {
//     name: "Pera",
//     price: "2.00",
//     description: "Una pera",
//     stock:10,
//     id: 2,
//   },
//   {
//     name: "Naranja",
//     price: "1.00",
//     description: "Una naranja",
//     stock:30,
//     id: 3,
//   },
// ];
// const objetoFruta = {
//   name: "Manzana",
//   price: "1.00",
//   description: "Una manzana",
//   id: 1,
// };
// const activo = false;

// //methods

// const handleClick = (message) => { console.log(message) };

const counter = ref(0);

const arrayFav = ref([]);


const increment = () => {
  // console.log('aumentar contador');
  counter.value++;
  // console.log(counter);
}

const decrement = () => {
  counter.value--;
}

const resetear = () => {
  counter.value = 0;
}

const add = () => {
  arrayFav.value.push(counter.value);
}

const deleteFavorito = () => {
  arrayFav.value.pop(counter.value);
};


const mostrar = computed(() => {
  const numSearch = arrayFav.value.find(num => num === counter.value);
  return numSearch || numSearch === 0;

});


const classCounter = computed(() => {
  if (counter.value === 0) {
    return 'inicial';
  }

  else if (counter.value > 0) {
    return 'increment';
  }

  else {
    return 'decrement';
  }


})

</script>

<template>
  <div style="padding-left: 1rem;">
    <h1>Hola {{ name.toUpperCase() }}</h1>
    <br>
    <h2 :class="classCounter"> {{ counter }}</h2>
    <br>
    <!-- <ul>
    <li v-for="(fruit, index) in arrayFruits" :key="index">
      {{ index }} - {{ fruit }}
    </li>
  </ul>
  <ul>
    <li v-for="fruta in arrayFrutas" :key="fruta.id">
      {{ fruta.name }} - {{ fruta.price }} - {{ fruta.description }}

    </li>
  </ul> -->
    <!-- <ul>
    <li v-for="(value, prop, index) of objetoFruta" :key="value">
      {{ index }} - {{ prop }}: {{ value }}
    </li>
  </ul> -->
    <!-- <ul>
    <template v-for="item in arrayFrutas" :key="item.name">
      <li v-if="item.stock > 0">{{ item.name }} - {{ item.price }}</li>
    </template>
</ul>
<h2>{{ arrayColores }}</h2>
<h2 :style="`color:${arrayColores[2]}`">Soy Azul</h2>
<h2>
  {{ activo ? "Hola" : name }}
</h2>
<h2 v-if="activo === true">Estoy activo</h2>
<p v-else-if="activo === false">Estoy inactivo</p>
<p v-else>Estoy indeciso</p>
<h2 v-show="activo">Estoy activo v-show</h2> -->
    <!-- <button @click="handleClick('Hola 1')">Activar 1 </button>
  <button @click="handleClick('Hola 2')">Activar 2 </button>
  <br>
  <br>
  <button v-on:click.left="handleClick('Texto Left')">Activar Left </button>
  <button @click.middle="handleClick('Texto Middle')">Activar Middle </button>
  <button @click.right.prevent="handleClick('Texto Right')">Activar Right </button> -->

    <button @click="decrement" class="btn btn-danger">Disminuir</button>
    <br>
    <br>
    <button @click="resetear" class="btn btn-secondary">Resetear</button>
    <br>
    <br>
    <button @click="increment" class="btn btn-success">Aumentar</button>
    <br>
    <br>
    <button @click="add" :disabled="mostrar" class="btn btn-primary">Add</button>
    <br>
    <br>
    <button @click="deleteFavorito"class="btn btn-danger">Delete Favorito</button>
    <br>
    <br>
    <ul class="list-group">
      <li class="list-group-item" v-for="(num, index) in arrayFav" :key="index">
        {{ num }}
      </li>
    </ul>
  </div>


</template>

<style>
h1 {
  color: red;
}

.decrement {
  color: red;
}

.increment {
  color: green;
}

.inicial {
  color: black;
}
</style>
