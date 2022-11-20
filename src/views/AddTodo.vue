<template>
  <div class="container">
    <div class="row">
      <div class="col p-3">
        <h2>Add Table</h2>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <div class="form-group">
          <label htmlFor="name_table">Table name :</label>
          <input type="text" class="form-control" v-model="state.todoitemlocal.name_table" />
        </div>
        <div class="form-group">
            <label htmlFor="desc">Description :</label>
            <textarea class="form-control" rows="3" id="desc" v-model="state.todoitemlocal.desc"></textarea>  
        </div>
        <div class="form-group">
            <button type="button" class="btn btn-primary m-1" @click="addTodo">Add</button>
            <button type="button" class="btn btn-primary m-1" @click="cancel">Cancel</button>
        </div>
      </div>
    </div>
  </div> 
</template>

<script>
import Constant from '../Constant';
import { reactive } from 'vue'
import { useStore } from 'vuex'
import { useRouter } from 'vue-router';

export default {
    setup() {
        const store = useStore();
        const router = useRouter();

        const state = reactive({ 
            todoitemlocal : { no:"", name_table:"", desc:"", done:false } 
        });

        const addTodo = () => {
          if (state.todoitemlocal.name_table.trim().length >= 2) {
            store.dispatch(Constant.ADD_TODO, { todoitem : state.todoitemlocal })
            router.push({ name:"todoList" });
          } else {
            alert('Enter the to-do in 2 characters or more');
          }
        }
        const cancel = () => {
            router.push({ name:"todoList"});
        }

        return { state, addTodo, cancel }
    }
}
</script>

<style>

</style>