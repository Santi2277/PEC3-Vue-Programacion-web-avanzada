<template>
  <form class="form">
    <div class="form__element">
        <ul>
            <li>
                <h4>Title:</h4>
                <input type="text" v-model="postIt.title" name="title">
            </li>
            <li>
                <h4>Message:</h4>
                <input type="text" v-model="postIt.message" name="message">
            </li>
            <li>
                <h4>Custom Color:</h4>
                <input type="checkbox" v-model="postIt.custom" name="custom">
            </li>
            <li>
                <h4>Color:</h4>
                <input type="color" v-model="postIt.color" name="color">
            </li>
             <li>
                <input type="submit" value="submit" name="add" v-on:click.prevent="onSubmit">
            </li>
        </ul>
    </div>
  </form>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';

export default {
  name: 'PostItForm',
  data: function() {
  return {
    postIt: {
        id: undefined,
        title      : '',
        message  : '',
        custom  : false,
        color : undefined
    }
  };
  },  
  methods: {
    onSubmit(){
      //alert("Submit clicked. Message: " + this.postIt.message);
      if(!this.postIt.custom){
          this.postIt.color = undefined;
      }
      this.postIt.id = uuidv4();
      
      //alert("Submit clicked. Id: " + this.postIt.id);
      this.$emit("add-postit", { postIt: {id: this.postIt.id, title: this.postIt.title, message: this.postIt.message, color: this.postIt.color} });

      //clean form values
      this.postIt.title = '';
      this.postIt.message = '';
      this.postIt.custom = false;
      this.postIt.color = undefined;
      this.postIt.id = undefined;
    }
  }
}
</script>

<style scoped>
ul {
list-style-type: none;
padding: 0;
}
li {
display: inline-block;
margin: 0 10px;
}
.form {
padding: 15px;
}
.form {
padding: 15px;
}
.form__element {
display: flex;
flex-direction: column;
margin-bottom: 15px;
text-align: left;
}
.form__element label {
margin-bottom: 10px;
font-weight: bold;
}
</style>