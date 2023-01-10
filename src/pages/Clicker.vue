<template>
  <div class="columns ">
      <div class="column is-half has-text-centered" >
          <b>{{displayCookies}} cookies</b>
          <br>
          <b> {{displayCps}} cookies per second</b>
        <img @click="cookieClick" :class="{ 'click' : ClickClass}" src="https://www.picng.com/upload/cookie/png_cookie_11811.png" >
      </div>
      <div class="column is-one-third ">
          <button @click="upgrade(0.1, 10)" class="button is-primary" :disabled="cookies < 10">Buy 0.1 cps for 10 cookies</button>
          <button @click="upgrade(1, 100)" class="button is-primary" :disabled="cookies < 100">Buy 1 cps for 100 cookies</button>
          <button @click="upgrade(10, 1000)" class="button is-primary" :disabled="cookies < 1000">Buy 10 cps for 1000 cookies</button>
          <button @click="upgrade(100, 10000)" class="button is-primary" :disabled="cookies < 10000">Buy 100 cps for 10000 cookies</button>
          <button @click="upgrade(1000, 100000)" class="button is-primary" :disabled="cookies < 100000">Buy 1000 cps for 100000 cookies</button>
      </div>
  </div>
</template>

<script>
export default {
    created(){
        setInterval(()=> {
                this.cookies +=  this.cps;
                this.cookies = parseFloat(this.cookies.toFixed(1));
        }, 1000);
    },
      data(){
          return{
              ClickClass: false,
              cookies: 0,
              cps: 0
          }
      },
      computed: {
          displayCookies(){
              return parseFloat(this.cookies.toFixed(1));
          },
          displayCps(){
              return parseFloat(this.cps.toFixed(1));
          },
      },
      methods: {
          cookieClick(){
              this.cookies++ ;
              this.ClickClass = true;
              setTimeout(()=> {
                       this.ClickClass = false;
              }, 250);
          },
          upgrade(cps, cost){
          if(this.cookies >= cost){
              this.cookies -= cost;
              this.cps += cps;
          }
      }
      },
      
}
</script>

<style scoped>
    img { 
        cursor:grab;
    }
    img.click {
         transform: scale(0.9); 
         cursor: grabbing ;
         content: url('https://static.vecteezy.com/system/resources/previews/009/400/072/original/homemade-tasty-cookies-clipart-design-illustration-free-png.png');

    }
   
</style>
