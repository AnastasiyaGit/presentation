<template>
  <div id="main">
    <Transition >
    <div :key="currentEl" class="row gx-sm-2 gx-md-5 align-items-center justify-content-center" style="height: 100%">
<!--      :class="'col-'+ 12/currentStep.length"-->
<!--      :class="'col-3'"-->
<!--      <TransitionGroup name="fade" tag="div" class="row gx-5 align-items-center justify-content-center" style="height: 100%">-->
      <div :class="'col-'+ 12/currentStep.length"  v-for="(item,index) in currentStep" :key="item.id">
        <one-item  v-model="currentStep[index]" @chooseEl="goToNext"></one-item>
      </div>
<!--      </TransitionGroup>-->
    </div>
    </Transition>
  </div>

</template>

<script setup>
import OneItem from "@/views/home/copmonents/OneItem.vue";
import {onMounted, ref} from "vue";
const currentStep= ref([])
const currentEl = ref(false)
const firstStep = ref([{name:'Voltage',id:1,finish:false},{name:'Current',id:2,finish:false}])
// const secondStep = ref([{name:'Voltage',id:3,finish:false},{name:'Current',id:4,finish:false}])
const thirdStep = ref([{name:'AC',id:5,finish:false},{name:'AC/DC',id:6,finish:false}])
const forthStep = ref([{name:'<30 A',id:7,finish:false},{name:'30 - 100 A',id:8,finish:false},{name:'>100 A',id:9,finish:false}])
const fifthStep = ref([{image:'TCP0150.jpg',id:10,finish:true,name:'TCP404XL',params:'Maximum Current: 500 A DC; 500 A RMS; 750 A peak\n' + 'Bandwidth: DC - 2 MHz',link:'https://www.tek.com/en/datasheet/ac-dc-current-measurement-systems'},
  {image:'TCP404XL.jpg',id:11,finish:true,name:'TCP0150',params:'Maximum Current: 150 A DC; 150 A RMS; 500 A peak\n' + 'Bandwidth: DC - 20 MHz',link:'https://www.tek.com/en/datasheet/tcp0150-ac-dc-current-probe-datasheet'}])
const goToNext = (id)=>{
  console.log(id)
  currentEl.value = id
    switch (id) {
      case 2:
        currentStep.value= thirdStep.value
        break;
      case 6:
        currentStep.value= forthStep.value
        break;
      case 9:
        currentStep.value= fifthStep.value
        break;
    }
}
onMounted(()=>{
  currentStep.value= firstStep.value
  currentEl.value = currentStep.value[0].id
})
</script>

<style scoped>
#main{
  padding: 30px 0;
  height: calc(100vh - 60px);

}
.v-enter-active{
  transition: all 2s linear;
}
.v-leave-active {
  transition: all 0.5s linear;
}

.v-enter-from,
.v-leave-to {
  /*transform: translateX(30px);*/
  opacity: 0;
}




.fade-enter-active{
  transition: opacity  1s ease;
}
.fade-leave-active {
  transition: opacity  1s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  /*transform: translateX(30px);*/
}
</style>
