<template>
<form @submit.prevent="onSubmit()">
  <div class="form-group">

    <input type="text"
    name="title"
    placeholder="Title"
    v-model="poll.title"
    required>

  </div>
  <div
  v-for="(option, index) in poll.options" 
  :key="index"  class="form-group">

    <input type="text" 
    :name="`option${index + 1}`"
    :placeholder="`Option ${index + 1}`"
    v-model="poll.options[index]"
    required>

    <button
    type="button"
    class="btn btn-link"
    @click="remove(index)"
    v-if="poll.options.length > 2">
      Remove
    </button>

  </div>
  <div class="form-group">

    <button
    type="button"
    class="btn btn-link"
    @click="add()">
      Add
    </button>

  </div>
  <input type="submit">
</form>
</template>

<script>
export default {
  // on nomme notre component
  name: 'create',
  // la fonction data retourne les données INTERNES de notre component, data DOIT être une fonction
  data(){
    return {
      poll: {
        title: "",
        options: ["",""]
      }
    }
  },
  // on déclare les méthodes du component
  methods: {
    // la méthode onSubmit() est appelée lorsqu'on submit le formulaire
    onSubmit(){
      console.log(this.poll)
    },
    // la méthode add() est appelée lorsqu'on clique sur le bouton "add"
    add(){
      // on ajoute une string vide dans le tableau options, ce qui ajoutera un input dans notre formulaire
      this.poll.options.push("")
    },
    // la méthode remove() est appelée lorsqu'on clique sur le bouton "remove"    
    remove(index){
      // on retire du tableau l'élément correspodant à l'index
      this.poll.options.splice(index, 1)
    }
  }
}
</script>

<style scoped>
</style>
