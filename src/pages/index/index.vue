<template>
  <div>
    <ul>
      <li
        v-for="(item,index) in list"
        :key="index"
        @longtap="delOne(index)"
      >{{item.name}}----{{item.age}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "index",
  data: function() {
    return {
      list: [
        { name: "hehe", age: 20 },
        { name: "ksks", age: 13 },
        { name: "momo", age: 120 }
      ]
    };
  },
  methods: {
    delOne(index) {
      wx.showModal({
        title: "提示",
        content: "确认删除吗",
        success:(res) =>{
          if (res.confirm) {
            this.list.splice(index,1)
          } else if (res.cancel) {
            console.log("用户点击取消");
          }
        }
      })
     
    }
  }
};
</script>

<style>
</style>
