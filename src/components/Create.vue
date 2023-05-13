<template>

<form @submit.prevent="submitForm">
  <div class="form-group m-b">
    <label for="name">Task</label>
    <input type="text" class="form-control" v-model="name">
  </div>
  <div class="form-group">
    <label for="input2">Description</label>
    <input type="text" class="form-control" v-model="description">
  </div>
  <button type="submit" class="btn btn-primary" @click="createObject">Submit</button>
</form>

</template>

<script>
export default {
data(){
    return {
        name: '',
        description: '',
    }
},
methods: {
    createObject()
    {
        const newArray = new Object()
        newArray.name = this.name
        newArray.description = this.description
        this.name = '';
        this.description = '';
        this.$emit('array-passed', newArray);

    },
    submitForm() {
      // handle form submission here
      
    }
}
}
</script>