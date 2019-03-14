<style lang="stylus" scoped>
.blackhole
  width 100%
  height 100%
  background #ffffff
  min-height 100vh
  overflow hidden
.black
  position fixed
  width 0px
  height 0px
  left 951px
  top 408px
  position relative
  animation rotates 15s linear infinite
@keyframes rotates
  from
    transform rotate(0deg)
  to
    transform rotate(360deg)
.box
  position relative
  li
    position absolute
    z-index 2
    list-style none
    transition all 3s
    &:nth-child(1)
      left 30px
      top 500px
      width 120px
      height 90px
    &:nth-child(2)
      left 30px
      top 650px
      width 120px
      height 90px
    &:nth-child(3)
      left 230px
      top 650px
      width 120px
      height 90px
    &:nth-child(4)
      left 230px
      top 500px
      width 120px
      height 90px  
    &:nth-child(5)
      left 850px
      top 165px
      width 90px
      height 90px  
    &:nth-child(6)
      left 960px
      top 165px
      width 90px
      height 90px  
    &:nth-child(7)
      left 1070px
      top 165px
      width 90px
      height 90px  
    &:nth-child(8)
      left 1080px
      top 165px
      width 120px
      height 90px  
    img 
      width 100%
      height 100%
</style>

<template>
  <div class="blackhole" @click="open">
    <div class="box">
      <img id="black" :src="blackholeimg" class="black">
      <ul>
        <li v-for="(arr, index) in arrs" :key="index">
          <img :src="arr.img">
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
var timer, timer1;
export default {
  data(){
    return{
      arrs:[
        {
          img:'img/0.jpeg'
        },
        {
          img:'img/1.jpeg'
        },
        {
          img:'img/2.jpeg'
        },
        {
          img:'img/3.jpg'
        },
        {
          img:'img/4.jpeg'
        },
        {
          img:'img/5.jpeg'
        },
        {
          img:'img/6.jpeg'
        },
        {
          img:'img/7.jpeg'
        },
      ],
      blackholeimg:'img/blackhole.png',
      myopen:false
    }
  },
  methods:{
    // 点击屏幕黑洞动画开启
    open(){
      // 防止多次点击
      if(this.myopen) {
        return false
      }
      this.myopen = true;
      // 设置增量
      let i = 0
      // 获取元素
      let black = document.getElementById('black');
      let allli = document.getElementsByTagName('li')
      // 设置黑洞中心点
      let cx = document.documentElement.clientWidth/2;
      let cy = document.documentElement.clientHeight/2;
      let mx = cx;
      let my = cy;

      // 黑洞出现动画
      timer = setInterval(() => {
        i += 2;
        cx -= 1
        cy -= 1
        this.move(black,i, cx, cy)
        // 判断黑洞大小
        if(i > 650) {
          clearInterval(timer);
          setTimeout(() => {
            timer1 = setInterval(() => {
              i += 2;
              cx -= 1
              cy -= 1
              this.move(black,i, cx, cy)
              // 判断黑洞大小
              if(i > 1500) {
                clearInterval(timer1);
                let timer2 = setInterval(() => {
                  i -= 2;
                  cx += 1
                  cy += 1
                  this.move(black,i, cx, cy)
                  if(i < 1) {
                    clearInterval(timer2);

                  }
                },2)
              }
            }, 4)
          }, 200);
          for(let i = 0; i < allli.length; i++){
            allli[i].style.left = `${mx}px`
            allli[i].style.top = `${my}px`
            allli[i].style.width = '0px'
            allli[i].style.height = '0px'
          }
        }
      }, 10)
    },
    // 黑洞移动
    move(black,i, cx, cy){
      black.style.width = `${i}px`;
      black.style.height = `${i}px`;
      // 设置黑洞位置
      black.style.left = `${cx}px`;
      black.style.top = `${cy}px`;
    }
  }
}
</script>
