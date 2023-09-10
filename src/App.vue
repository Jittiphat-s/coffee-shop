<script setup>
import { ref } from 'vue';

// ตัวแปร
//const travel = ref("");
const money = ref(0);
const nameuser = ref("");
const tel = ref("");
const table = ref("");
const time = ref("");

// const travellist=ref(['Forest Bake','Dong Madame','Chocolate Ville','ร้านชวนพิศมัย','Potpuree'])
 const travellist=ref([
  { name: 'Forest Bake', price:40 , size: {s:40, m:150, l: 200 }, img: "https://scontent.fbkk5-4.fna.fbcdn.net/v/t1.6435-9/33074613_569116693459527_9140572063889620992_n.jpg?_nc_cat=110&ccb=1-7&_nc_sid=8bfeb9&_nc_eui2=AeG2dXzobGLRixHwfAtgxkAwEt0qzcLon4gS3SrNwuifiD63iaIinHkQp_SjPRCyZ31Ibxw17f5OP4_jORc972MS&_nc_ohc=yC003Fp9iPIAX-ywCEY&_nc_ht=scontent.fbkk5-4.fna&oh=00_AfCqwJ3VZcYRvExVoQ1uw_ikWDh58jngGwYe7HYNdTJMJA&oe=6522C0C7" },
  { name: 'Dong Madame', price:50 , size: {s:50, m:160, l: 210 }, img:"https://scontent.fbkk5-8.fna.fbcdn.net/v/t1.18169-9/13880350_293707491006536_6615723173717939268_n.jpg?_nc_cat=106&ccb=1-7&_nc_sid=9267fe&_nc_eui2=AeHRkxK8qEqwPci6bzjIBzi1yZsbV-c8bw7JmxtX5zxvDjub5d1vxxn9RMEklVDU_dUOYbmZxaBP1xUoPn6JdaR4&_nc_ohc=As99sShj7Z0AX8CazsZ&_nc_ht=scontent.fbkk5-8.fna&oh=00_AfAR-p2OidhEhlyuGclMAmC4dpbZkaduH4cTOg1SWEismA&oe=6522CF8B"},
  { name: 'Chocolate Ville', price:100 , size: {s:100, m:200, l: 300 }, img:"https://cms.dmpcdn.com/travel/2017/11/01/f1e783f0-e8bf-11e9-822c-45ab57972f75_original.jpg"},
  { name: 'ร้านชวนพิศมัย', price:150 , size: {s:100, m:150, l: 200 }, img:"https://cms.dmpcdn.com/travel/2017/11/01/f1e6e7b0-e8bf-11e9-b6ac-ad412d87f3d2_original.jpg"},
  { name: 'Potpuree', price:1000 , size: {s:1000, m:1500, l: 10000 }, img:"https://cms.dmpcdn.com/travel/2017/03/06/f2deabc0-d786-46c6-8177-de7f3b4a2ab4.jpg"},
  
]);
//เก็บข้อมูลการจองร้าน
const bookinglist = ref([
  //"Chocolate Ville","ร้านชวนพิศมัย"
]);

// function
function booking(name){
  // name --> +. bookinglist[]
  bookinglist.value.push(name)

}



</script>


<template>
  
    <div class="text-center">
      <div class="row row-cols-1 row-cols-md-3 g-4">
        <div class="col" v-for="(i, index ) in travellist" :key="index">
                  <div class="card text-bg-secondary n-100" style="width:18rem">
                    <img v-if="i.img" :src="i.img" class="card-img-top" alt="..." />
                      <div class="card-body">
                        <h5 class="card-title">{{ i.name }}</h5>
                        <p class="card-text" >
                          จำนวนโต๊ะ <input  typy="text" v-model="table">
                        </p>
                        <p class="card-text" >
                          ชื่อผู้จอง <input  typy="text" v-model="nameuser">
                        </p>
                        <p class="card-text">
                          เบอร์โทร<input typy="text" v-model="tel">
                        </p>
                        <p class="card-text">
                          วันที่<input typy="text" v-model="date">
                        </p>
                        <p class="card-text">
                          เวลา<input typy="text" v-model="time">
                        </p>
                        <a class="btn btn-danger" @click="booking( i.name )">จองโต๊ะ</a> 
                      </div>
                  </div>
        </div>
      </div>
      
    </div>


    


    
  <div>
    <div class="p-3 m-0 border-0 bd-example m-0 border-0"></div>

    <table class="table table-secondary table-striped" v-if="bookinglist.length > 0">
  <thead>
    <tr>
      <th scope="col">ลำดับ</th>
      <th scope="col">ชื่อผู้จอง</th>
      <th scope="col">เบอร์โทร</th>
      <th scope="col">จำนวนโต๊ะ</th>
      <th scope="col">วันที่</th>
      <th scope="col">เวลา</th>
      <th scope="col">รายชื่อ-ร้านที่จอง</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(item, index, ) in bookinglist" :key="index">
      <td scope="=row">{{ index+1 }}</td>
      <td scope="row">{{ nameuser }}</td>
      <td scope="row">{{ tel }}</td>
      <td scope="row">{{ table }}</td>
      <td scope="row">{{ date }}</td>
      <td scope="row">{{ time }}</td>
      <td>{{ item }}</td>
    </tr>

  </tbody>
</table>

    <button typy="button" class="btn btn-primary">Primary</button>
    <div v-for="(i, index) in travellist" :key="index">
      {{ index+1 }}
      ชื่อ {{ i.name }}
      size M = {{ i.size.m }}
      ราคา {{ i.price }}
      ชื่อผู้จอง{{ i.nameuser }}
      เบอร์โทร {{ i.tel }}
      วันที่{{ i.date }}
      เวลา {{ i.time }}
      จำนวนโต๊ะ {{ i.table }}
      รูป
      แผนที่
    </div>




    <h1>ร้านกาแฟ</h1>
      <input type="radio" value="a" v-model="travel" />ร้านกาเเฟใกล้ฉัน
      <input type="radio" value="b" v-model="travel" />ร้านกาแฟเเนะนำ
      <br  />

       จำนวนเงิน
      <input type="number" v-model="money">
      <br  />

      <p v-if="money<100">ไปร้านกาเเฟเเนะนำราคาถูกใกล้ฉัน!</p>
      <p v-else-if="money>=100 && money<9999">ไปร้านกาเเฟร้านเเนะนำราคาเเพงใกล้ฉัน!</p>
      <p v-else>ไปร้านกาเเฟสุดหรู!</p>

      <button v-if="money < 50" type="" disabled>เดินทางไปร้านราคาเเพง</button>
      <button v-else type="">เดินทางไปร้านราคาเเพง</button>

      <div v-if="travel == 'a'">ร้านกาเเฟใกล้ฉัน</div>
      <div v-else>ร้านกาแฟเเนะนำ</div>
  </div>

</template>