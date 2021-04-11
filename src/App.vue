<template>
  <div class="container" @click="$emit('close-add-tour')">
      <AppHeader @open-add-tour = "isOpen=true" @close-add-tour="isOpen=false" />
      <div class="main">
          <ul>
              <li v-for="(tour,index) in state.tours" :key="index">
              <img :src="tour.image" :alt="tour.name"/>
              <p><small>Name:</small> {{tour.name}}</p>
              <p><small>Location:</small> {{tour.country}}</p>
              <p><small>Price:</small> {{tour.price}}$</p>
              <small>Information:{{tour.info}}</small>
              <button @click="remove(index)">Not Interested</button>
              </li>
          </ul>
      </div>
      <form  @close-add-tour = "isOpen=false" v-if="isOpen" class="create" @submit.prevent="addTour">
          <div class="form-header">
            <h2>ADD TOUR</h2>
          </div>
          <div class="child">
            <p>Name</p>
            <input v-model="state.newName" placeholder="add new tour"/>
          </div>
          <div class="child">
            <p>Country</p>
            <input v-model="state.newCountry" placeholder="add tour's country"/>
          </div>
          <div class="child">
            <p>Prices</p>
            <input v-model="state.newPrice" placeholder="add tour's price"/>
          </div>
          <div class="child">
            <p>Info</p>
            <input v-model="state.newInfo" placeholder="add tour's info"/>
          </div>
          <div class="child">
            <p>Image</p>
            <input v-model="state.newImage" placeholder="add tour's image link"/>
          </div>
          <div class="btn">
            <button  @close-add-tour = "isOpen=false" type="submit">Add</button>
          </div>
      </form>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader'
import { reactive} from '@vue/reactivity'

export default {
  components:{
    AppHeader
  },
  setup(){
    const state = reactive({
      tours : [
        {
        name:"Eiffel",
        country:"France",
        price:"3000",
        image:"https://www.kkhotels.com/wp-content/uploads/2020/01/Paris-City-Eiffeltower-View.jpg",
        info:"The Eiffel Tower is a wrought-iron lattice tower on the Champ de Mars in Paris, France. It is named after the engineer Gustave Eiffel, whose company designed and built the tower"
        },
        {
          name:"London Eye",
          country:"United Kingdom",
          price:4000,
          image:"https://res.klook.com/images/fl_lossy.progressive,q_65/c_fill,w_3000,h_2000,f_auto/w_80,x_15,y_15,g_south_west,l_klook_water/activities/ikknf4oeysojhyv2z0jk/V%C3%A9V%C3%B2ngQuayLondonEye.jpg",
          info:"The London Eye, or the Millennium Wheel, is a cantilevered observation wheel on the South Bank of the River Thames in London. It is Europe's tallest cantilevered observation wheel, and is the most popular paid tourist attraction in the United Kingdom with over 3 million visitors annually."
        },
        {
          name:"The Great Wall of China",
          country:"China",
          price: 2500,
          image:"https://hoc247.net/fckeditorimg/upload/images/great-firewall-1-600x400.jpg",
          info:"The Great Wall of China is a series of fortifications that were built across the historical northern borders of ancient Chinese states and Imperial China as protection against various nomadic groups from the Eurasian Steppe."
        },
        {
          name:"Pisa Tower",
          country:"Italy",
          price:2700,
          image:"https://upload.wikimedia.org/wikipedia/commons/f/f2/Leaning_Tower_of_Pisa.jpg",
          info:"The Leaning Tower of Pisa or simply the Tower of Pisa is the campanile, or freestanding bell tower, of the cathedral of the Italian city of Pisa, known worldwide for its nearly four-degree lean, the result of an unstable foundation."
        }
      ],
      newName:"",
      newCountry:"",
      newPrice:"",
      newInfo:"",
      newImage:""
    })
    function addTour(){
      state.tours.push({name:state.newName,country:state.newCountry,price:state.newPrice,info:state.newInfo,image:state.newImage}),
      state.newName = "",
      state.newCountry="",
      state.newImage="",
      state.newPrice="",
      state.newInfo=""
    }
    function remove(index){
      state.tours = state.tours.filter((tour, i) => i != index);
    }
    return{state ,remove,addTour}
  },
  data(){
    return{
      isOpen :false,
    }
  }
}
</script>

<style>
*{
  margin:0;
}
li p{
  padding:5px;
}
.form-header{
  font-family: "Poppins",sans-serif;
}
button{
  margin:10px;
  padding:6px;
  background-color: transparent;
  border:none;
  border-radius: 20px;
  box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.5);
  font-size: smaller;
}
li{
  height: 500px;
  width:500px;
  padding:10px;
  background-color: #f5f5f3;
  margin:10px;
  display:flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  font-family: "Poppins",sans-serif;
  box-shadow: 0px 2px 2px rgba(0,0,0,0.5);
}
ul img{
  height: 350px;
  width:350px;
}
.header{
  height: 40px;
  background-color: white;
  display:flex;
  align-items: center;
  padding:10px;
  font-family: "Poppins",sans-serif;
  box-shadow: 0 2px 2px rgba(0,0,0,.5);
  letter-spacing: 5px;
}
.main{
  height: 90vh;
  overflow-y: scroll;
}
form{
  top:9.5vh;
  position: absolute;
  display:flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  height:700px;
  width: 700px;
  z-index:100;
  background-color:white;
}
form input{
    height: 25px;
    margin-top:5px;
    margin-bottom: 5px;
    border-bottom:2px solid black;
    border-top:none;
    border-right:none;
    border-left:none;
    outline:none;
    width: 400px;
}
.container{
  top:0;
  left:0;
  right:0;
  bottom:0;
  display:flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  position: relative;
  z-index: 10;
}
</style>