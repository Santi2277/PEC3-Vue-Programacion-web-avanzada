<template>
  <div class="board">
    <!-- <post-it id="1" title="Nota 1" message="Contenido de la nota 1" @delete-postit="eventHandler"/> -->
    <div v-for="postIt in postItList" v-bind:key="postIt.id">
      <post-it :postIt="postIt" @delete-postit="eventHandler"/>
    </div>

  </div>

</template>

<script>
import PostIt from './PostIt.vue'

export default {
  name: 'Board',
  components: {
    PostIt
  },
  props: ["postItList"],
  methods: {
    eventHandler(postIt){
      //alert(`Post It deleted (Board component). Id: ${postIt.id}`);
      this.$emit("delete-postit", { id: postIt.id });
    }
  }
}
</script>

<style scoped>
.board {
background-color: #464344;
border: 10px solid #a5792a;
height: 100%;
padding: 25px;
display: flex;
flex-wrap: wrap;
justify-content: space-around;
}
</style>