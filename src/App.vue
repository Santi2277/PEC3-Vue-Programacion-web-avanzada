<template>
  <div id="app">
    <div class="header">
      <img alt="logo-uoc" src="./assets/logo-uoc.png"  width="50" height="50">
      <h1 class="app-name">Post-It Board - PEC 2</h1>
    </div>

      <div class="column-left">
        <board :postItList="postItList" @delete-postit="deletePostIt"/>
      </div>
      <div class="column-right">
        <post-it-form @add-postit="addPostIt"/>
      </div>
  </div>
</template>

<script>
import Board from './components/Board.vue'
import PostItForm from './components/PostItForm.vue'

export default {
  name: 'App',
  components: {
    Board,
    PostItForm
  },
  data: function() {
  return {
    postItList: [
      {
         id: 1,
        title: "Title",
        message: "Message",
        color: "#CCCCCC"
        
       },
      {
        id: 2,
        title: "Title 2",
        message: "Message 2",
        color: "#CCCCCC"
        
      }
    ]
  };
  },
  methods: {
    deletePostIt(postIt){
      alert(`Post It deleted (App component). Id: ${postIt.id}`);
      for( var i = 0; i < this.postItList.length; i++){ 
    
        if ( this.postItList[i].id === postIt.id) { 
    
            this.postItList.splice(i, 1); 
        }
    
    }
      
    },
    addPostIt(postIt){
      alert(`Post It added with ID: ${postIt.postIt.id}`);
      this.postItList.push(postIt.postIt);
      
    }
  }
}
</script>

<style>
#app {
font-family: Avenir, Helvetica, Arial, sans-serif;
-webkit-font-smoothing: antialiased;
-moz-osx-font-smoothing: grayscale;
text-align: center;
color: #2c3e50;
display: flex;
flex-wrap: wrap;
height: 100%;
}
.header {
width: 100%;
padding: 15px;
display: flex;
align-items: center;
}
.header .logo {
max-height: 50px;
}
.header .app-name {
margin-left: 25px;
font-weight: bold;
font-size: 20px;
}
.column-left {
width: 80%;
}
.column-right {
width: 20%;
}
</style>
