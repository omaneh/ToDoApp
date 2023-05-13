<template>
<nav class="navbar navbar-expand-lg navbar-light bg-light">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">To Do App</a>
  </div>
</nav>
<div class="container mt-5">
<h4>Current List</h4> 
<div v-if="create">
<div class="container mb-5" >
  <Create @array-passed="onArrayPassed"/>
  </div>
  </div>
  <div v-else>
  <button class="btn red" @click="CreateNow"><i class="fa fa-caret-square-o-up" aria-hidden="true">Create</i></button>
  </div>
  <div class="container mt-3" >
  <div class="container border">
    <div class="table">
  <div class="row header border">
    <div class="col">Name</div>
    <div class="col">Description</div>
    <div class="col"></div>
  </div>
  <div class="row mt-2" v-for="item in list">
    <div class="col">{{item.name}}</div>
    <div class="col">{{item.description}}</div>
    <div class="col"><button class="btn btn-outline-* border-0" @click="Delete(item)">Delete</button></div>
    </div>
  </div>
  </div>
  </div>

  </div>
</template>

<script>
import Create from './components/Create.vue';
export default {
    data() {
        return {
            list: [],
            create: false
        };
    },
    methods: {
        onArrayPassed(newArray) {
            this.list.push(newArray);
            this.create = false
        },
        CreateNow() { 
          this.create = true
        },
        Delete(item)
        {
          const index = this.list.indexOf(item)
          this.list.splice(index, 1)
        }
    },
    components: { Create }
}
</script>