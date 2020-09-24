<template>
  <div id="app">
    <h1>IP Calculator</h1>
    <hr>
    <h2>Список ip диапазонов</h2>
    <AddDataIp
            @add-todo="addDataIp"
    />
    <ListIP
            v-bind:dataIp="dataIp"
            @remove-dataIp="removeDataIP"
    />

    <hr>
    <button v-on:click="genListIp">исключить IP</button>
    <NewListIp
            v-bind:dataIp="ipList"
    />
    <hr>

  </div>
</template>

<script>
import ListIP from '@/components/ListIP'
import AddDataIp from '@/components/AddDataIp'
import NewListIp from '@/components/NewListIp'


export default {
  name: 'App',
  data(){
    return {
      dataIp: [
        {id: 1, ip1: '92.168.1.1', ip2: '122.168.2.238'},
        {id: 2, ip1: '19.168.8.1', ip2: '19.168.3.28'},
        {id: 3, ip1: '250.168.25.1', ip2: '252.168.25.238'}
      ],
      ipList: []
    }
  },
  methods:{
    removeDataIP(id){
      this.dataIp = this.dataIp.filter(t => t.id !== id )
    },
    addDataIp(ip){
      this.dataIp.push(ip)
    },
    genListIp(){
      let i = 0;
      let newlist =[]
      while (i < 500) {
        let genIp = this.getRandomInt(1, 255)+'.'+this.getRandomInt(1, 255)+'.'+this.getRandomInt(1, 255)+'.'+this.getRandomInt(1, 255)
        if(this.checkValid(genIp)==true){
          newlist.push(genIp+'/'+this.genMask(genIp))
        }
        i++;

      }
      this.ipList = newlist
    },
    getRandomInt(min, max) {
      return Math.floor(Math.random() * (max - min)) + min;
    },
    genMask(ip){
      let parseIp = ip.split(".")
      console.log(parseIp)
      if(Number(parseIp[3])==255)
        return 32
      if(Number(parseIp[3])==254)
        return 31
      if(Number(parseIp[3])>=252)
        return 30
      if(Number(parseIp[3])>=248)
        return 29
      if(Number(parseIp[3])>=240)
        return 28
      if(Number(parseIp[3])>=224)
        return 27
      if(Number(parseIp[3])>=192)
        return 26
      if(Number(parseIp[3])>=128)
        return 25
      if(Number(parseIp[3])>=0)
        return 24
      if(Number(parseIp[2])==254)
        return 23
      if(Number(parseIp[2])>=252)
        return 22
      if(Number(parseIp[2])>=248)
        return 21
      if(Number(parseIp[2])>=240)
        return 19
      if(Number(parseIp[2])>=224)
        return 18
      if(Number(parseIp[2])>=192)
        return 17
      if(Number(parseIp[2])>=128)
        return 16
      if(Number(parseIp[1])>=0)
        return 15
      if(Number(parseIp[1])==254)
        return 14
      if(Number(parseIp[1])>=252)
        return 13
      if(Number(parseIp[1])>=248)
        return 12
      if(Number(parseIp[1])>=240)
        return 11
      if(Number(parseIp[1])>=224)
        return 10
      if(Number(parseIp[1])>=192)
        return 9
      if(Number(parseIp[1])>=128)
        return 8
      if(Number(parseIp[0])==255)
        return 7
      if(Number(parseIp[0])==254)
        return 6
      if(Number(parseIp[0])>=252)
        return 5
      if(Number(parseIp[0])>=248)
        return 4
      if(Number(parseIp[0])>=240)
        return 3
      if(Number(parseIp[0])>=224)
        return 2
      if(Number(parseIp[0])>=192)
        return 1
      if(Number(parseIp[0])>=0)
        return 0


    },
    checkValid(ip){
      let parseIp = ip.split(".")
      this.dataIp.forEach(function(item) {
        let parseIp1 = item.ip1.split(".");
        let parseIp2 = item.ip2.split(".");

        if(Number(parseIp1[0])<=Number(parseIp[0])&&Number(parseIp[0])<=Number(parseIp2[0])){
          return  false;
        }

      });
      return true
    }
  },
  components: {
    ListIP, AddDataIp, NewListIp
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  max-width: 90%;
  padding: 0 5%;
}
</style>
