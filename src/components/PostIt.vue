<template>
  <div class="postit">
    <div class="postit-inner" v-bind:style="{ backgroundColor: postIt.color}">
        <h3 class="title">{{ postIt.title }}</h3>
        <p class="note">{{ postIt.message }}</p>
        <button class="close" v-on:click="deletePostIt(postIt.id)">
            Delete Post It
        </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PostIt',
  props: ["postIt"],
  methods: {
    deletePostIt(id){
      this.$emit("delete-postit", { id: id });
    }
  }
}
</script>

<style scoped>

.postit {
    text-decoration: none;
    color: #000;
    display: block;
    transform: rotate(-6deg);
    text-align: left;
    margin: 15px;
}
.postit-inner {
height: 10em;
width: 10em;
background: #ffc;
padding: 15px;
box-shadow: 5px 5px 7px rgba(33, 33, 33, 0.7);
}
.postit:nth-child(even) {
transform: rotate(4deg);
position: relative;
top: 5px;
}
.postit:nth-child(3n) {
transform: rotate(-3deg);
position: relative;
top: -5px;
}
.postit:nth-child(5n) {
transform: rotate(5deg);
position: relative;
top: -10px;
}
.close {
    cursor: pointer;
}
.close:before {
content: "x";
position: absolute;
right: 10px;
top: 2px;
font-size: 20px;
}
.note {
font-family: "Reenie Beanie", arial, sans-serif;
font-size: 20px;
}
h3 {
margin-top: 0;
margin-bottom: 10px;
}
p {
margin-top: 0;
}
</style>