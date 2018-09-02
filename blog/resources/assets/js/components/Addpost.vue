<template id="add-post">
  <div>
    <h3> Add Post </h3>
    <form v-on:submit.prevent = "createPost" >

   <div class="form-group">
        <label for="add-title"> Nom </label>
        <input id="add-nom" v-model="post.nom" class="form-control" required>
      </div>

      <div class="form-group">
        <label for="add-title"> Prenom </label>
        <input id="add-prenom" v-model="post.prenom" class="form-control" required>
      </div>

      <div class="form-group">
        <label for="add-title"> mail </label>
        <input id="add-mail" v-model="post.mail" class="form-control" required>
      </div>

      <div class="form-group">
        <label for="add-title"> telephone </label>
        <input id="add-tel" v-model="post.tel" class="form-control" required>
      </div>

      <div class="form-group">
        <label for="add-title"> Title fonction </label>
        <input id="add-title" v-model="post.title" class="form-control" required>
      </div>

      <div class="form-group">
        <label for="add-title"> BODY </label>
        <input id="add-body" v-model="post.body" class="form-control" required>
      </div>

      <button type="submit" class="btn btn-xs btn-primary"> CREATE POST </button>
      <router-link class="btn btn-xs btn-warning" v-bind:to=" '/'"> CANCEL </router-link>

    </form>

  </div>
</template>

<script>
export default {
  data:function() {
  return {post: {nom:'', prenom:'', mail:'', tel:'', title:'', body:''}}
  //return {post: {title:'', body:''}}
  },
  methods:{
    createPost: function(){
      let uri = 'http://localhost:8000/posts/';
      Axios.post(uri, this.post).then((response) => {
        this.$router.push({name:'Listposts'})
      });
    }
  }
}
</script>

<style lang="css">
</style>
