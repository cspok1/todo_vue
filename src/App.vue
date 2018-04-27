<template>
  <div id="app">
    <div class="container">
      <h1>{{ title }}</h1>
      <br>
      <form @submit.prevent="addToDo">
  <div class="form-group">
    <label>What would you like to do?</label>
    <input type="text" class="form-control" id="toDoName" placeholder="" v-model="toDoName">
  </div>
  <br>
  <div class="form-group">
    <label for="exampleInputPassword1">Description</label>
    <textarea type="text" class="form-control" id="toDoDescription" placeholder="Add description..." rows="2" v-model="toDoDescription"></textarea>
  </div>
  <button class="btn btn-primary" type="submit">Submit</button>
</form>
    

    <br>
    <hr>
    <br>

    <ul class="list-group">
  <li class="list-group-item" v-for="todo in toDos">
    <h3 :class="{ done: todo.done }"><input type="checkbox" v-model="todo.done"> {{ todo.title }}</h3>
    <p><small>{{ todo.description }}</small></p>
    <button class="btn btn-primary" @click="removeToDo(todo)">Remove</button>
  </li>
</ul>

  </div>
  </div>
</template>

<script>
export default {
  data:function(){
    return {
    title: 'To-do List',
    toDoName: '',
    toDoDescription:'',
    toDos : []
    }
  },
  methods:{
    addToDo(){
      this.toDos.push({
        title: this.toDoName,
        description: this.toDoDescription,
        done: false
      });
      this.toDoName = ''
      this.toDoDescription = '' 
    },
  removeToDo(todo){
    var index = this.toDos.indexOf(todo);
    this.toDos.splice(index, 1)
  }
  }
}
</script>

<style>
.done{
  color:gray;
}

</style>
