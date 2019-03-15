<style lang="stylus" scoped>
.ParticleClock {
  margin-top: -1px;
  width: 100%;
  height: 100%;
  min-height: 100vh;
  background: #4fc3ad;
}

#canvas {
  display: block;
  background: #000;
  margin: 0px auto;
}
</style>

<template>
  <div class="ParticleClock">
    <canvas id="canvas" width="600" height="500"></canvas>
  </div>
</template>

<script>
class Draw{
  constructor(el){
    this.el = el
    this.canvas = document.getElementById(this.el)
    this.cxt = this.canvas.getContext('2d');
    this.cW = this.canvas.width = 600
    this.cH = this.canvas.height = 100
  }
  init(digit,num,index){
    // 遍历数字粒子
    for(let i = 0;i < digit[num].length; i++){
      for (let j = 0; j < digit[num][i].length; j++) {
        if(digit[num][i][j] === 1){
          this.drawing(index,num,i,j)
        }
      }
    }
  }
  drawing(index,num,i,j){
    let R = (this.cH/20) - 1;
    this.cxt.fillStyle = '#fff';
    this.cxt.beginPath()
    this.cxt.arc(14*(R+1)*index+j*2*(R+1)+(R+1), i*2*(R+1)+(R+1), R, 0, 2*Math.PI, false)
    this.cxt.closePath()
    this.cxt.fill()
  }
  clear(){
    this.cxt.clearRect(0, 0, 600, 100)
  }
}
export default {
  mounted(){
    this.gettime()
  },
  data(){
    return{
      digit :[
        [
          [0,0,1,1,1,0,0],
          [0,1,1,0,1,1,0],
          [1,1,0,0,0,1,1],
          [1,1,0,0,0,1,1],
          [1,1,0,0,0,1,1],
          [1,1,0,0,0,1,1],
          [1,1,0,0,0,1,1],
          [1,1,0,0,0,1,1],
          [0,1,1,0,1,1,0],
          [0,0,1,1,1,0,0]
        ],//0
        [
          [0,0,0,1,1,0,0],
          [0,1,1,1,1,0,0],
          [0,0,0,1,1,0,0],
          [0,0,0,1,1,0,0],
          [0,0,0,1,1,0,0],
          [0,0,0,1,1,0,0],
          [0,0,0,1,1,0,0],
          [0,0,0,1,1,0,0],
          [0,0,0,1,1,0,0],
          [1,1,1,1,1,1,1]
        ],//1
        [
          [0,1,1,1,1,1,0],
          [1,1,0,0,0,1,1],
          [0,0,0,0,0,1,1],
          [0,0,0,0,1,1,0],
          [0,0,0,1,1,0,0],
          [0,0,1,1,0,0,0],
          [0,1,1,0,0,0,0],
          [1,1,0,0,0,0,0],
          [1,1,0,0,0,1,1],
          [1,1,1,1,1,1,1]
        ],//2
        [
          [1,1,1,1,1,1,1],
          [0,0,0,0,0,1,1],
          [0,0,0,0,1,1,0],
          [0,0,0,1,1,0,0],
          [0,0,1,1,1,0,0],
          [0,0,0,0,1,1,0],
          [0,0,0,0,0,1,1],
          [0,0,0,0,0,1,1],
          [1,1,0,0,0,1,1],
          [0,1,1,1,1,1,0]
        ],//3
        [
          [0,0,0,0,1,1,0],
          [0,0,0,1,1,1,0],
          [0,0,1,1,1,1,0],
          [0,1,1,0,1,1,0],
          [1,1,0,0,1,1,0],
          [1,1,1,1,1,1,1],
          [0,0,0,0,1,1,0],
          [0,0,0,0,1,1,0],
          [0,0,0,0,1,1,0],
          [0,0,0,1,1,1,1]
        ],//4
        [
          [1,1,1,1,1,1,1],
          [1,1,0,0,0,0,0],
          [1,1,0,0,0,0,0],
          [1,1,1,1,1,1,0],
          [0,0,0,0,0,1,1],
          [0,0,0,0,0,1,1],
          [0,0,0,0,0,1,1],
          [0,0,0,0,0,1,1],
          [1,1,0,0,0,1,1],
          [0,1,1,1,1,1,0]
        ],//5
        [
          [0,0,0,0,1,1,0],
          [0,0,1,1,0,0,0],
          [0,1,1,0,0,0,0],
          [1,1,0,0,0,0,0],
          [1,1,0,1,1,1,0],
          [1,1,0,0,0,1,1],
          [1,1,0,0,0,1,1],
          [1,1,0,0,0,1,1],
          [1,1,0,0,0,1,1],
          [0,1,1,1,1,1,0]
        ],//6
        [
          [1,1,1,1,1,1,1],
          [1,1,0,0,0,1,1],
          [0,0,0,0,1,1,0],
          [0,0,0,0,1,1,0],
          [0,0,0,1,1,0,0],
          [0,0,0,1,1,0,0],
          [0,0,1,1,0,0,0],
          [0,0,1,1,0,0,0],
          [0,0,1,1,0,0,0],
          [0,0,1,1,0,0,0]
        ],//7
        [
          [0,1,1,1,1,1,0],
          [1,1,0,0,0,1,1],
          [1,1,0,0,0,1,1],
          [1,1,0,0,0,1,1],
          [0,1,1,1,1,1,0],
          [1,1,0,0,0,1,1],
          [1,1,0,0,0,1,1],
          [1,1,0,0,0,1,1],
          [1,1,0,0,0,1,1],
          [0,1,1,1,1,1,0]
        ],//8
        [
          [0,1,1,1,1,1,0],
          [1,1,0,0,0,1,1],
          [1,1,0,0,0,1,1],
          [1,1,0,0,0,1,1],
          [0,1,1,1,0,1,1],
          [0,0,0,0,0,1,1],
          [0,0,0,0,0,1,1],
          [0,0,0,0,1,1,0],
          [0,0,0,1,1,0,0],
          [0,1,1,0,0,0,0]
        ],//9
        [
          [0,0,0,0,0,0,0],
          [0,0,1,1,1,0,0],
          [0,0,1,1,1,0,0],
          [0,0,1,1,1,0,0],
          [0,0,0,0,0,0,0],
          [0,0,0,0,0,0,0],
          [0,0,1,1,1,0,0],
          [0,0,1,1,1,0,0],
          [0,0,1,1,1,0,0],
          [0,0,0,0,0,0,0]
        ]//:
      ] 
    }
  },
  methods:{
    gettime(){
      let newbox = new Draw('canvas')
      setInterval(() => {
        let myDate = new Date();
        newbox.clear()
        let h = myDate.getHours();
        let m = myDate.getMinutes();
        let s = myDate.getSeconds();
        let h1 = Math.floor(h/10)
        let h2 = h%10
        let m1 = Math.floor(m/10)
        let m2 = m%10
        let s1 = Math.floor(s/10)
        let s2 = s%10
        newbox.init(this.digit,h1,0)
        newbox.init(this.digit,h2,1)
        newbox.init(this.digit,10,2)
        newbox.init(this.digit,m1,3)
        newbox.init(this.digit,m2,4)
        newbox.init(this.digit,10,5)
        newbox.init(this.digit,s1,6)
        newbox.init(this.digit,s2,7)
      }, 1000)
    }
  }
}
</script>
