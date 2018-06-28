<template>
  <div id="app">
   <div v-for="item in items" :key="item.id">
     <img v-bind:src="imgpath(item)" alt="">
          <a v-bind:href="item.pageurl" target="_blank">
    <h1 style>  {{item.title}}</h1>
    <h2 style>  {{item.author}}</h2>
   </a>
   </div>
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld'
var catid=parseInt(window.location.href.split("=").pop());
import Firebase from 'firebase'
let config= {
   YOUR_FIREBASE_CONFIGURATION
}
let app= Firebase.initializeApp(config);
let db =app.database()
let itemRef = db.ref("items")
export default {
  name: 'App',
  firebase:{  
    items: itemRef
       //items: itemRef.orderByChild('categoryid').equalTo(catid),
  },
  methods:{
    imgpath: function(i){
      return "/static/images/" + i.imgname + ".jpg";
    }
  }
}
</script>

<style scoped>

#app {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  

}
#app div{
  width: 300px;
  height: 185px;
  border: solid 1px gray;
  border-radius: 2px;
  margin: 0.5em;
  top: 110px;
  box-shadow: 2px 2px 2px silver;
  position: relative;

}
#app div img{
  position:absolute;
  display: block;
  width: 100%;
  height: 100%;
  z-index: 10;
}
#app div h1{
  position: absolute;
  z-index: 15;
  margin: 0;
  top: 0;
  left:8px;
  font-size: 18pt;
}
#app div h1{
  position: absolute;
  z-index: 15;
  margin: 0;
  top: 24;
  left:8px;
  font-size: 14pt;
}
#app div a{
  display: block;
  position: absolute;
  z-index: 20;
  background:linear-gradient(black,transparent);
  color: white;
  width: 100%;
  height: 100%;
  text-shadow: 1px 1px black;
}
</style>
