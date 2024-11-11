<template>
<div :class="!model.finish ? 'item' : 'item-finish '" @click="emit('chooseEl',model.id)">
<!--  <div class="inner-item">-->
  <div class="title" >
    <h2 v-if="!model.finish" class="text-center mb-0" >{{model.name}}</h2>
    <div class="row " v-else>
      <div class="col-6">
          <img  :src="'/media/image/' + model.image" width="80%" class="scale">
      </div>
      <div class="col-6" style="place-content: center;">
        <a :href="model.link" target="_blank"><h5 style="font-weight: bold;">{{model.name}}</h5></a>
        <div style="color: #000000">{{model.params}}</div>
      </div>
    </div>

  </div>



<!--  <div class="content d-flex align-items-center justify-content-center">-->
<!--    <i class="bi bi-shuffle icon" ></i>-->
<!--  </div>-->
<!--  </div>-->
</div>
</template>

<script setup>
const model = defineModel()
const emit = defineEmits(['chooseEl'])
</script>

<style scoped lang="scss">

.title{
  height: 50px;
}
.content{
  height: 150px;
}
.icon{
  font-size: 3rem;
  color: #1CB5D8;
}
//1 variant
//.item{
//  position: relative;
//  cursor: pointer;
//  padding: 15px 7px;
//  height: 400px;
//  border-radius: 15px;
//  border: 2px solid #d7d7d7;
//  background: #ffffff;
//  transition: box-shadow 1s ease;
//}
//.item:hover{
//  background: #1CB5D8;
//  box-shadow: 0px 4px 10px 5px rgba(0, 0, 0, .2);
//  box-shadow: 0 15px 25px 10px rgba(0, 0, 0, .2);
//  transition: .5s;
//  top: -4px;
//}
//.item:hover .icon{
//  color:#ffffff;
//}

//2variant
//.item {
//  padding: 0px 30px;
//  cursor: pointer;
//  height: 400px;
//  //display: grid;
//  place-content: center;
//  color: #1CB5D8;
//  //text-shadow: 0 2px 0 #000;
//  text-shadow: 0 2px 1px #000;
//  --border-angle: 0turn;
//  --main-bg: conic-gradient(
//          from var(--border-angle),
//          #fff 50%,
//          #fff 5%,
//          #fff 60%,
//          #fff 95%
//  );
//  border: solid 6px transparent;
//  border-radius: 1.5em;
//  --gradient-border: conic-gradient(from var(--border-angle), transparent 25%, #1CB5D8, #0b607f 99%, transparent);
//  background: var(--main-bg) padding-box, var(--gradient-border) border-box, var(--main-bg) border-box;
//  background-position: center center;
//  -webkit-animation: bg-spin 5s linear infinite;
//  animation: bg-spin 5s linear infinite;
//}
//@-webkit-keyframes bg-spin {
//  to {
//    --border-angle: 1turn;
//  }
//}
//@keyframes bg-spin {
//  to {
//    --border-angle: 1turn;
//  }
//}
//.item:hover {
//  -webkit-animation-play-state: paused;
//  animation-play-state: paused;
//}
//@property --border-angle {
//  syntax: "<angle>";
//  inherits: true;
//  initial-value: 0turn;
//}



//4 vatiant
.item-finish {
  padding: 30px;
  color: #1CB5D8;
  //text-shadow: 0 2px 1px #676464;
  cursor: pointer;
  position: relative;
  height: 300px;
  place-content: center;
  transition: box-shadow 1s ease;
  .title{
    padding: 0 20px;
    box-shadow: 0px 4px 7px 4px rgba(0, 0, 0, 0.2);
    border-radius: 6px;
    place-content: center;
    border: 2px solid #26b3d6;
    height: 90%;
    a{
      text-decoration: none;
      color: #1CB5D8;
    }
  }
}
.scale {
  transition: 1s; /* Время эффекта */
}
.scale:hover {
  transform: scale(2); /* Увеличиваем масштаб */
}

.item {
  padding: 30px;
  color: #1CB5D8;
  text-shadow: 0 2px 1px #676464;
  cursor: pointer;
  position: relative;
  height: 300px;
  place-content: center;
  //background-color: #f0f0f0;
  transition: box-shadow 1s ease;
  .title{
    box-shadow: 0px 4px 7px 4px rgba(0, 0, 0, 0.2);
    border-radius: 6px;
    place-content: center;
    border: 3px solid #26b3d6;
    height: 70%;
  }
}

.item::before, .item::after,.item-finish::before, .item-finish::after {
  content: '';
  position: absolute;
  width: 50px;
  height: 50px;
  background-color: transparent;
  border: 2px solid #1CB5D8;
  transition: all 0.3s ease;
}

.item::before,.item-finish::before {
  top: 0;
  left: 0;
  border-right: none;
  border-bottom: none;
}
.item::after,.item-finish::after {
  bottom: 0;
  right: 0;
  border-left: none;
  border-top: none;
}
.item:hover::before {
  transform: translate(-15px, -15px);
}
.item:hover::after {
  transform: translate(15px, 15px);
}
.item:hover{
  box-shadow: 0px 4px 7px 4px rgba(0, 0, 0, .2);
  //box-shadow: 0 15px 25px 10px rgba(0, 0, 0, .2);
  transition: .5s;
  top: -4px;
  .title{
    color:#ffffff;
    background: #26b3d6;
  }
}
</style>
