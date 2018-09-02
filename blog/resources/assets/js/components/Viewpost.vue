<template id="post">
  <div>
    <h3> {{post.title}} </h3>

    <div>
      {{post.id}}
    </div>

    <div>
      {{post.nom}}
    </div>


    <div>
      {{post.prenom}}
    </div>

    <strong> Body : </strong>
    <div>
      {{post.body}}
    </div>

    <br>

    <span class="glyphicon glyphicon-arrow-left"></span>
    <router-link v-bind:to="'/'">Back to post link </router-link>
  </div>
</template>

<script>
export default{
  data: function () {
    return {post: {nom:'', prenom:'', title: '', body: ''}};
  },
  created: function() {
    let uri = 'http://localhost:8000/posts/'+ this.$route.params.id;
    Axios.get(uri).then((response) => {
      this.post = response.data;
    });
  }
}
</script>

<style lang="css">
</style>
