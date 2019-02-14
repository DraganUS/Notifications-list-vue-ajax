<template>
  <header>

    <div class="navbar navbar-dark bg-dark shadow-sm" >
        <a href="#" class="navbar-brand d-flex align-items-center" @click="ajaxCal()">
          <li class="nav-item dropdown" >
            <a class="nav-link dropdown-toggle" data-toggle="dropdown" href="#" role="button" >Notification <i class="fas fa-comment-alt"></i></a>
            <div class="dropdown-menu"  >
              <div class="notificationBox" v-for="(value, index) in item"  v-bind:class="value">
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
          message : 'loading...',
          seen: "false",
          timestamp: 1527959349
        }
      ]
    }
  },
  methods: {
    ajaxCal(){
      console.log('API call');
      fetch("https://api.myjson.com/bins/19wyhe")
    .then(response => response.json())
    .then((data) => {
      this.item = data;
    })
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
div.seen{
  background: gray;
}
</style>
