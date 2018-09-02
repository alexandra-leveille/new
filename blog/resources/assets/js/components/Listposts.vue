<template id="post-list">
<div class="row">
<div class="pull-right">
  <router-link class="btn btn-xs btn-primary" v-bind:to="{path:'add-post'}">
<span class="glyphicon glyphicon-plus"></span>
Add New Post
  </router-link>
  <br><br>
</div>

<table class="table table-bordered">
  <thead>
    <tr>
    <th> #</th>
    <th> Nom </th>
    <th> Prenom </th>
    <th> mail </th>
    <th> Telphone </th>
    <th> Post Title </th>
    <th> Post Body </th>
    <!-- <th> comment </th> -->
    <th class="col-md-2"> Actions </th>
    </tr>
  </thead>

  <tbody>
    <tr v-for="(post, index) in filteredPosts">
        <td> {{ post.id }} </td>
        <td> {{ post.nom }} </td>
        <td> {{ post.prenom }} </td>
        <td> {{ post.mail }} </td>
        <td> {{ post.tel }} </td>
        <td> {{ post.title }} </td>
        <td> {{ post.body }} </td>
        <!-- <td> {{post.prenom}} est le {{post.title}} numero {{post.id}} </td> -->
        <td>
<router-link class="btn btn-info btn-xs" v-bind:to="{name:'Viewpost', params: {id: post.id}}"> SHOW </router-link>
<router-link class="btn btn-warning btn-xs" v-bind:to="{name:'Editpost', params: {id: post.id}}"> EDIT</router-link>
<router-link class="btn btn-danger btn-xs" v-bind:to="{name:'Deletepost', params: {id: post.id}}"> DELETE </router-link>
        </td>
    </tr>
  </tbody>
</table>

</div>
</template>

<script>
export default {
  data: function(){
    return {posts: ''};
  },
  created: function(){
    let uri = 'http://localhost:8000/posts/';
    Axios.get(uri).then((response) => {
      this.posts = response.data;
    });
  },
  computed: {
    filteredPosts: function(){
      if (this.posts.length) {
        return this.posts;
      }
    }
  }
}
</script>

<style lang="css">

</style>
