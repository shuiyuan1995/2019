<style lang="stylus" scoped>
.swiper
  perspective 800px
.wrap
  width 133px
  height 200px
  margin 150px auto 
  position relative
  transform-style preserve-3d
  transform rotateX(-20deg)
  img 
    width 100%
    height 100%
    position absolute
    transition transform .5s ease
</style>

<template>
  <div class="swiper" ondragstart="return false">
    <div class="wrap" id="wrap">
      <img v-for="(arr, index) in arrs" :key="index"
      :src="arr.img" alt="">
    </div>
  </div>
</template>

<script>
export default {
  mounted(){
    // 初始化
    window.onload = () => {
      this.init()
    }
  },
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
        {
          img:'img/8.jpeg'
        },
        {
          img:'img/9.jpeg'
        },
      ],
      // 旋转度数
      rotateX:-20,
      rotateY:0,
    }
  },
  methods:{
    init(){
      // 获取元素
      let oImg = document.getElementsByTagName("img");
      let imgL = this.arrs.length
      let deg = 360/imgL
      // 循环设置
      for (let i = 0; i < imgL; i++) {
        // 设置旋转
        let countdeg = deg*i;
        oImg[i].style.transform = `rotateY(${countdeg}deg) translateZ(350px)`
        // 计算延迟
        let delaytime = imgL - i
        oImg[i].style.transitionDelay=`${delaytime/10}s`
      }
      // 开启拖拽
      this.drag()
    },
    // 拖拽动作
    drag(){
      // 鼠标按下
      let self = this
      document.onmousedown = function(e) {
        // 鼠标点击位置
        let oldx = e.clientX
        let oldy = e.clientY
        // 鼠标移动
        this.onmousemove = e => {
          // 移动坐标
          let x = e.clientX
          let y = e.clientY
          // 旋转度数
          self.rotateY += (x - oldx)/10
          self.rotateX += (y - oldy)/10
          document.getElementById('wrap').style.transform = `rotateY(${self.rotateY}deg) rotateX(${self.rotateX}deg)`
          oldx = x
          oldy = y
        }
        // 鼠标松开
        this.onmouseup = () => {
          this.onmousemove = null;
        }
      }
    }
  }
}
</script>
