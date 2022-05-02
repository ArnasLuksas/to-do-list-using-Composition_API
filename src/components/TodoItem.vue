<script setup>
import { ref } from "vue";
const items = ref([
  { id: 1, name: "Learn Vue.js" },
  { id: 2, name: "Make a project" },
]);
const item = ref("");

//push item from input to items array
const addToList = () => {
  items.value.push({ id: items.value.length + 1, name: item.value });
  //reset input to empty
  item.value = "";
};

//remove (splice()) item from array by index
const removeItem = (item) => {
  items.value.splice(items.value.indexOf(item), 1);
};
</script>
<template>
  <div>
    <input type="text" v-model="item" placeholder="to do" />
    <button @click="addToList">Add</button>
    <ul>
      <li v-for="item in items" :key="item.id">
        {{ item.id }}. {{ item.name }}
        <button @click="removeItem(item)">Remove</button>
      </li>
    </ul>
  </div>
</template>