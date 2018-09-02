<template id="post-edit">
  <div>
    <h3> Edit Post </h3>
    <form v-on:submit.prevent = "updatePost" >


      <div class="form-group">
        <label for="edit-title"> nom </label>
        <input id="edit-nom" v-model="post.nom" class="form-control" required>
      </div>

      <div class="form-group">
        <label for="edit-title"> prenom </label>
        <input id="edit-prenom" v-model="post.prenom" class="form-control" required>
      </div>

      <div class="form-group">
        <label for="edit-title"> mail </label>
        <input id="edit-mail" v-model="post.mail" class="form-control" required>
      </div>

      <div class="form-group">
        <label for="edit-title"> tel </label>
        <input id="edit-tel" v-model="post.tel" class="form-control" required>
      </div>

      <div class="form-group">
        <label for="edit-title"> Title </label>
        <input id="edit-title" v-model="post.title" class="form-control" required>
      </div>

      <div class="form-group">
        <label for="edit-body"> Body </label>
        <textarea class="form-control"  rows="10" v-model="post.body"></textarea>
      </div>

      <button type="submit" class="btn btn-xs btn-primary"> UPDATE POST </button>
      <router-link class="btn btn-xs btn-warning" v-bind:to=" '/'"> CANCEL </router-link>
    </form>

  </div>
</template>

<script>
export default {
  data: function () {
    return {post: {nom:'', prenom:'', mail:'', tel:'', title:'', body:''}}
  },
  created: function(){
    let uri ='http://localhost:8000/posts/'+ this.$route.params.id + '/edit';
    Axios.get(uri).then((response) => {
      this.post = response.data;
    });
  },
  methods: {
    updatePost: function(){
      let uri = 'http://localhost:8000/posts/'+ this.$route.params.id;
      Axios.patch(uri, this.post).then((response) => {
        this.$router.push({name:'Listposts'})
      });
    }
  }
}
</script>
