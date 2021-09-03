<template>
  <div>
    <marquee direction="right">Develope By SK SAYED AKTAR</marquee>
    <h1> 📝 Todo List 📝 </h1>
    <center>
      <table>
        <tr v-for="item in items" :key="item.id">
          <td style=""><b>{{item.name}}:</b></td><td style="padding-left: 10px;">{{item.desc}}</td><td style="padding-left:20px;"><button type="button" v-on:click="itemDelete(item.id)" class="btn btn-sm btn-outline-danger">Delete</button></td>
        </tr>
      </table>
    </center>
    <center>
      <div class="addTask">
        <div class="input-group">
          <span class="input-group-text">Add a new Todo</span>
          <input type="text" v-model="items.name" aria-label="todo" placeholder="Enter the heading" class="form-control">
          <input type="text" v-model="items.desc" placeholder="Short Description" aria-label="todo" class="form-control">
          <button type="button" v-on:click="addItem" class="btn mx-5 btn-outline-success">Add item</button>
        </div>
      </div>
    </center>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return{
      items:[
        {"id":1, "name": "Sample Heading", "desc": "Sample Description"},
      ]
    }
  },
  methods: {
    itemDelete(itemid){
      this.items = this.items.filter((obj)=>{
        return obj.id !== itemid;
      })
    },
    addItem(){
      var itemname = this.items.name;
      var itemDesc = this.items.desc;
      var itemId = this.items.length;

      this.items.push({"id":itemId, "name":itemname, "desc":itemDesc});
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  margin-bottom: 40px;
}

div.addTask{
  margin-left: 25%;
  margin-right: 25%;
  margin-top: 25px;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
*{
  padding:0px;
  margin:0px;
}
</style>
