<template>
  <header>

    <div class="navbar navbar-dark bg-dark shadow-sm" >
        <a href="#" class="navbar-brand d-flex align-items-center" @click="ajaxCal()">
          <li class="nav-item dropdown" >
            <a class="nav-link dropdown-toggle" data-toggle="dropdown" href="#" role="button" >Notification <i class="fas fa-comment-alt"></i></a>
            <div class="dropdown-menu"  >
              <div class="notificationBox" v-for="(value) in item">
                <img v-bind:src="value.icon" alt="" >
                 <a class="dropdown-item" href="#">{{ value.message }}</a>
              </div>
            </div>
          </li>
        </a>
    </div>

  </header>
</template>

<script>
export default {
  data(){
    return {
      item: [
         {
          icon: "http://icons.iconarchive.com/icons/martz90/circle/256/messages-icon.png",
          message : 'test 1',
          seen: "false",
          timestamp: 1527959349
        },
        {
          icon: "http://icons.iconarchive.com/icons/martz90/circle/256/messages-icon.png",
          message : 'test 2',
          seen: "false",
          timestamp: 1527959349
        }
      ]
    }
  },
  methods: {
    ajaxCal(){
      console.log('API call');
      console.log("this is ithem", this.item)
      
      var request = new XMLHttpRequest();
      request.open('GET', 'https://api.myjson.com/bins/19wyhe');
      request.onload = handleResponse;
      request.send();

      function handleResponse(){
          
        var newData = JSON.parse(request.response);
        console.log(newData.length);
        var result = [];      
        console.log("novi ",result);
        for (var i = 0; i < newData.length; i++) {  
          console.log(newData[i]);
                result.push({
                icon: newData[i].icon,
                message: newData[i].message,
                seen: newData[i].seen,
                timeout: newData[i].timeout
             });  
          }


      }
    }
  }
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
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
a.nav-link::after{
  display: none;
}
div.notificationBox{
  box-sizing: border-box;
  padding: 10px;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  border-bottom: 1px solid #d2d2d3;
}
.dropdown-menu{
  padding: 3px 15px;
}
div.notificationBox img{
  height: 30px;
  /* margin: 10px; */
}
</style>
