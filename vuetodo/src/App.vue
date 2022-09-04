<template>
  <div class="badass-todo">
    <div class="title has-text-centered">
      Badass-todo
    </div>
<form action="" @submit.prevent="addTodo">
  <div class="field is-grouped">
  <p class="control is-expanded">
    <input v-model="newTodoContent" class="input" type="text" placeholder="Add a todo here">
  </p>
  <p class="control">
    <button :disabled="!newTodoContent" type="submit" class="button is-info">
      Add
    </button>
  </p>
</div>
</form>
<div v-for="i in todo" class="card my-3">
  <div class="card-content">
    <div class="content">
      <div class="columns is-mobile is-vcentered">
        <div class="column ">
        {{ i.content }}
        </div>
        <div class="column is-5 has-text-right">
          <button class="button is-light">
          &check;
          </button>
          <button @click="deleteTodo(i.id)" class="button is-danger">
            &cross;

          </button>
        </div>
      </div>

      

    </div>
  </div>
</div>
  </div>
</template>

<script setup>
import { ref  } from "vue"
import { v4 as uuidv4 } from 'uuid'

const todo = ref([
  {
    id:"id1",
    content:"first todo",
    done:false
  }
  ,  {
    id:"id2",
    content:"second todo",
    done:false
  },  {
    id:"id3",
    content:"third todo",
    done:false
  }
])
const newTodoContent = ref('')
const addTodo = () =>{
    const newTodo = {
      id: uuidv4(),
      content: newTodoContent.value,
      done: false
    }

      todo.value.unshift(newTodo)
      newTodoContent.value=""
  }
  const deleteTodo = (id) =>{
      todo.value = todo.value.filter((todo)=>todo.id !==id) 
  }
</script>


<style>
@import '../node_modules/bulma/css/bulma.min.css';
.badass-todo{
  width: 500px;
  margin: 20px auto;
}

</style>
