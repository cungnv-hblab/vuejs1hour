<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Menu/>
    <!-- 
      the input va div in ra cung 1 du lieu la name. Vue co chưc năng 2 ways binding. Ở data ở tầng dưới
      thay đổi thì tầng trên thay đổi và ngược lại. Ví dụ nếu thay đổi name ở file nay thì in ra cũng thay đổi.
      Do name là dữ liệu được dùng ở cả thẻ div và input nên khi ta viết thay đổi trong input thì name trong thẻ
      div cũng thay đổi theo mặc dù ta k thay đổi giá trị của input ->Thay đổi theo chiều từ trên xuống dưới
      -> Điểm khác nhau cả vue và react
     -->
    <input type='text' v-model='name'>
    <!--
      tên v-show phải đặt như thế do là thuộc tính của vue. Nếu true thì hiện, k thì thôi
    -->
    <div v-bind:id='id' v-show='isShow'>Made by {{name}}</div>
    <button @click="isShow=!isShow">Click to hidden or show</button>
    <input type='text' v-model='name' :disabled='iputDisable' :class="{text_red:iputDisable}">
    <button @click="iputDisable=!iputDisable">Open/Close</button>
  </div>
</template>

<script>
import Menu from './components/Menu.vue'

export default {
  // ham data se tra ve mot obj chua du lieu ta muon xu ly. Ví dụ khi get api thì để data vào biến name
  //hoặc tên biến nào đấy rồi ở trên lấy xử lý
  data(){
    return {
      name:'Nguyen Van A',
      isShow:true,
      id:'test',
      xyz:'hello',
      iputDisable:true,
    }
  },
  /**
    Nhìn vào sơ đồ lifecycle nếu muốn viết sự kiện nào thì override lại. Ví dụ trước khi data thay đổi muốn làm
    gì đấy thì viết lại hàm beforeUpdate(). Cứ viết lạ đúng tên hàm vào đúng thời điểm mà ta muôn.
  */
  components: {
    Menu
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
}
.text_red{
  background-color:#2ABE3A
}
</style>
