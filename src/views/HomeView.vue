<template>
  <div id="homeWrapper">
    <v-app>
     <my-header/>
      <v-main>
        <div>
          <v-select
        :items="items"
        label="city 1"
        v-model="filter"
        >
        </v-select>
        <v-select 
        :items="items2"
        label="city 2"
        v-model="filter2"
        ></v-select>
        <div class="dateWrapper">
          <label id="dateLabelone">date1</label>
         <Datepicker v-model="date1" :minDate="new Date()" format="dd-MM-yyyy" id="datepicker"></Datepicker>
         <label id="dateLabeltwo">date2</label>
        <Datepicker v-model="date2" :minDate="date1" format="dd-MM-yyyy" ></Datepicker>
        </div>
        </div>
        <div>
          <my-body :flight="filteredRows"
          />
        </div>
      </v-main>
    </v-app>
  <my-footer id="ftr"/>
  </div>
</template>

<script>
// @ is an alias to /src

import MyFooter from '@/components/MyFooter.vue'
import MyBody from '@/components/MyBody'
import MyHeader from '@/components/MyHeader.vue'
import Datepicker from 'vue3-date-time-picker';
  import 'vue3-date-time-picker/dist/main.css';
  import { ref } from 'vue';
import moment from 'moment'


export default {
  name: 'HomeView',
  components: {
    MyHeader,
    MyBody,
    MyFooter,
    Datepicker
    
  },
  created: function(){
    this.moment = moment;
  },
  setup() {
        const date = ref(new Date());
        return{
          date,
        };
  },
  computed:{
      filteredRows(){
      return this.flight.filter(row=>{
        const departureCity = row.departureCity.toString().toLowerCase();
        const arrivalCity = row.arrivalCity.toString().toLowerCase();
        const departureDateTime = row.departureDateTime.toString();
        const arrivalDateTime = row.arrivalDateTime.toString();

        const searchItem = this.filter.toLowerCase();
        const searchItem2 = this.filter2.toLowerCase();

        const searchDate = moment(this.date1).format("DD-MM-YYYY").toString();
        const searchDate2 = moment(this.date2).format("DD-MM-YYYY").toString();
        

        if(searchItem=='' && searchDate=='Invalid date'){
        return (departureCity.includes(searchItem)&&
         arrivalCity.includes(searchItem2))||
         (departureDateTime.includes(searchDate)&&
         arrivalDateTime.includes(searchDate2))}
        else if (searchItem=='' && searchItem2==''){
         return (departureDateTime.includes(searchDate)&&departureDateTime.includes(searchDate2))||(
         arrivalDateTime.includes(searchDate2)||arrivalDateTime.includes(searchDate2))}
         return(departureCity.includes(searchItem)&&
         arrivalCity.includes(searchItem2))||
         (departureDateTime.includes(searchDate)&&
         arrivalDateTime.includes(searchDate2))
         }
      );
  }
  },
 data() {
    return {
    items:['','Ufa','Moscow','London','Beijing','Volgograd','New-York'],
    items2:['','Ufa','Moscow','London','Beijing','Volgograd','New-York'],
    
     date1:'',
     date2:'',
     filter:'',
     filter2:'',


      flight: [
        {
          id: 1,
          departureCity: 'Moscow',
          arrivalCity: 'London',
          departureDateTime: '04-03-2022',
          arrivalDateTime: '05-03-2022',
          cost: 4.0,
          
        },
        {
          id: 2,
          departureCity: 'Moscow',
          arrivalCity: 'Ufa',
          departureDateTime: '01-03-2022',
          arrivalDateTime: '06-03-2022',
          cost: 4.0,
          
        },
        {
          id: 3,
          departureCity: 'Moscow',
          arrivalCity: 'Beijing',
          departureDateTime: '02-03-2022',
          arrivalDateTime: '05-03-2022',
          cost: 4.0,
          
        },
        {
          id: 4,
         departureCity: 'Moscow',
          arrivalCity: 'Saint-Peterburg',
          departureDateTime: '05-03-2022',
          arrivalDateTime: '10-03-2022',
          cost: 4.0,
        },
        {
          id: 5,
          departureCity: 'Volgograd',
          arrivalCity: 'Moscow',
          departureDateTime: '03-03-2022',
          arrivalDateTime: '03-03-2022',
          cost: 4.0,
        },
        {
          id: 6,
          departureCity: 'Saint-Peterburg',
          arrivalCity:'Moscow',
          departureDateTime: '04-03-2022',
          arrivalDateTime: '05-03-2022',
          cost: 4.0,
          
        },
        {
          id: 7,
         departureCity: 'Moscow',
          arrivalCity: 'Volgograd',
          departureDateTime: '04-03-2022',
          arrivalDateTime: '08-03-2022',
          cost: 4.0,
          
        },
        {
          id: 8,
          departureCity: 'Beijing',
          arrivalCity: 'Moscow',
          departureDateTime: '10-03-2022',
          arrivalDateTime: '12-03-2022',
          cost: 4.0,
        },
        {
          id: 9,
          departureCity: 'New-York',
          arrivalCity:'Moscow',
          departureDateTime: '12-03-2022',
          arrivalDateTime: '13-03-2022',
          cost: 4.0,
        },
        {
          id: 10,
          departureCity: 'Moscow',
          arrivalCity: 'New-York',
          departureDateTime: '11-03-2022',
          arrivalDateTime: '13-03-2022',
          cost: 4.0,
          
        },
         {
          id: 1,
          departureCity: 'Moscow',
          arrivalCity: 'London',
          departureDateTime: '05-03-2022',
          arrivalDateTime: '08-03-2022',
          cost: 4.0,
          
        },
      ],
    }
  }
}

</script>

<style>
#homeWrapper{
display: grid;
grid-template-rows: 1fr 200px;
align-items: flex-end;
}
#dateLabeltwo{
margin-left:15px ;
}
.dateWrapper{
  display: grid;
  grid-template-columns:60px 200px 60px 200px;
  justify-content: center;
}

</style>