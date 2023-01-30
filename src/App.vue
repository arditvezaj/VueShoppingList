<template>
  <body>
    <div class="shopping-list">
      <h1>My Shopping List</h1>
      <ul>
        <li v-for="item in items" :key="item.id">
          {{ item.name }} <button id="btn" @click="removeItem(item)">X</button>
        </li>
      </ul>
      <div class="input">
        <input type="text" v-model="newItem" placeholder="Add Item" />
        <button @click="addItem">Add</button>
      </div>
    </div>
  </body>
</template>

<script setup>
import { ref } from "vue";

const items = ref([
  { id: 1, name: "Milk" },
  { id: 2, name: "Bread" },
  { id: 3, name: "Cheese" },
]);
const newItem = ref("");

function addItem() {
  if (newItem.value.length < 3) {
    return alert("You cannot add Items with less than 3 letters!");
  } else {
    items.value.push({
      id: items.value.length + 1,
      name: newItem.value,
    });
    newItem.value = "";
  }
}

function removeItem(item) {
  const index = items.value.indexOf(item);
  if (index > -1) {
    items.value.splice(index, 1);
  }
}
</script>

<style scoped>
body {
  background-color: rgb(182, 152, 187);
}
.shopping-list {
  display: flex;
  flex-direction: column;
  padding-top: 6rem;
  align-items: center;
  font-size: 1.5rem;
  color: rgb(62, 37, 86);
}
h1 {
  font-weight: bold;
}

ul {
  margin: 1rem;
}

li {
  display: flex;
  justify-content: space-between;
  font-size: 2rem;
  margin: 1rem 5rem 0 0;
}
.input {
  margin-top: 20px;
}
input {
  padding: 10px;
  font-size: 1.2rem;
  border: 1px solid gray;
  border-radius: 5px;
  margin-right: 10px;
}
button {
  padding: 10px 20px;
  font-size: 1.2rem;
  font-weight: bold;
  border-radius: 5px;
  background-color: rgb(74, 29, 90);
  color: white;
  border: none;
  cursor: pointer;
}

#btn {
  margin-left: 7rem;
  border-radius: 100%;
  font-size: 1rem;
  background-color: rgb(226, 79, 79);
}
</style>
