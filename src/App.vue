<template>
  <div id="app">
  <div class="header">
  <p>5 Ocak Tarihi #Efsel icin bir baslangic</p>
  <p class="subTitle">Efsel Yapılacaklar Listesi</p>

</div>
 <main class="mainSection">
      <div  class="grvDiv" >
        <input class="grvInpt"  v-model="task.name" />
        <button class="grvBtn" @click="addTask" >Görev Ekle Yavrum</button>
      </div>
 <div class="cardDiv" v-for="(item,index) in taskList" :key="index">
          <div class="card">
      <img src="data:image/jpeg;base64,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" alt="Biz"  />
      <div class="container">
      <div class="checkArea"><p>Görev Durumuuuu : <input @change="setTaskStatus(item)" type="checkbox" v-model="item.complate"/> {{!item.complate?"Aktif":"Görev Tamamlandııı"}}</p></div>
          <p class="cardText">{{index+1}} - {{item.name}}</p> 
      </div>
    </div>
          </div>

 </main>
  </div>
</template>

<script>
import axios from "axios"
export default {
  name: 'App',
  data(){
    return{
      taskList:[],
      task:{
        name:"",
        complate:false
      }
    }
  },
  methods:{
   async addTask(){
     debugger
   if(this.task.name.trim()==""){
      this.$toast.open({
    message: 'Boş Görev Ekleyemezsin Bal Kaymağımm Üzgünümmm',
    type: 'error',
     position: 'top'
    // all of other options may go here
});
      
       // error();
    }else{
    var yeni=await axios.post("https://efsel-2b3d4-default-rtdb.firebaseio.com/taks.json",{name:this.task.name,complate:false})
           this.$toast.open({
    message: 'Görev Eklendii Yavrummm',
    type: 'success',
     position: 'top'
    // all of other options may go here
});
      this.task.name=""
      this.task.complate=false;
      this.getTask();

    }
      },
      async setTaskStatus(item){
        debugger
            var s=await axios.put("https://efsel-2b3d4-default-rtdb.firebaseio.com/taks/"+item._id+".json",{name:item.name,complate:item.complate})
                    this.$toast.open({
    message: 'Görev Durumu Değiştii Ballı Çörekkk',
    type: 'success',
     position: 'top'
    // all of other options may go here
});
            console.log("sss",s)
      },
     async getTask(){
   var s=await axios.get("https://efsel-2b3d4-default-rtdb.firebaseio.com/taks.json")
    var x=Object.keys(s.data)
    var test=[]
    for (let index = 0; index < x.length; index++) {
      test.push({id:index,name:s.data[x[index]].name,_id:x[index],complate:s.data[x[index]].complate})
    }
    this.taskList=test;
      }
  },
  async created(){
    this.getTask();
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Hachi+Maru+Pop&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Homemade+Apple&display=swap');

.header {
  padding: 60px;
  text-align: center;
  background: #096dd9;
  color: white;
  font-size: 30px;
  font-family: 'Homemade Apple', cursive;
}
.subTitle{
  font-size: 14px;
}
.grvInpt{
  height: 40px;
  outline: none;
  width: 100%;
  box-sizing: border-box;
  padding: 20px;
}
.grvDiv{
margin-top: 20px;
  padding: 20px;
  display: flex;
  flex-direction: column;
}
.grvBtn{
  margin-top: 20px;
  height: 40px;
  line-height: 1.5715;
  position: relative;
  display: inline-block;
  font-weight: 400;
  white-space: nowrap;
  text-align: center;
  background-image: none;
  -webkit-box-shadow: 0 2px 0 rgba(0,0,0,.015);
  box-shadow: 0 2px 0 rgba(0,0,0,.015);
  cursor: pointer;
  -webkit-transition: all .3s cubic-bezier(.645,.045,.355,1);
  transition: all .3s cubic-bezier(.645,.045,.355,1);
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  -ms-touch-action: manipulation;
  touch-action: manipulation;
  height: 32px;
  padding: 4px 15px;
  font-size: 14px;
  border-radius: 2px;
  color: rgba(0,0,0,.85);
  background: #fff;
  border: 1px solid #d9d9d9;
  color: #fff;
  background: #1890ff;
  border-color: #1890ff;
  text-shadow: 0 -1px 0 rgba(0,0,0,.12);
  -webkit-box-shadow: 0 2px 0 rgba(0,0,0,.045);
  box-shadow: 0 2px 0 rgba(0,0,0,.045);
}
.cardDiv{
  padding: 20px;
}
.card {
  display: flex;
  flex-direction: column;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
  width: 100%;
}

.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
}

.container {
  padding: 20px;
}
.cardText{
  font-family: 'Hachi Maru Pop', cursive;
}
.checkArea{
  font-family: 'Hachi Maru Pop', cursive;

}
</style>
