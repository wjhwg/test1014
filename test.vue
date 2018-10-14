<template>
  <div>
    <ul v-for="(item, index) in results" :key="index">
      <li v-if="!item.isEdit" class="show1">
        <div class="it">{{item.name}}:{{item.content}}</div>
      </li>
    </ul>
    <ul v-for="(item, index) in datas" :key="index">
      <li v-if="item.name && item.content && item.change">
        <div class="it">{{item.name}}:{{item.content}}</div>
      </li>
    </ul>
     <div  v-for="(items, index) in datas" :key="index">
     <div v-if="items.isEdit && !items.change">
      <input placeholder="请输入name" v-model="items.name" /> ---- <input v-model="items.content" placeholder="请输入content"/>
      <span @click="del(index)">删除</span>
      </div>
      </div>
      <!-- <div v-for="item in con.change">{{item}}</div> -->
    <button @click="add()">添加</button>
    <button @click="save();">保存</button>
    <button @click="change();">修改</button>
  </div>
</template>

<script>
import hel from './hel'
import {datas} from './haha'
export default {
  // name: 'HelloWorld',
  data () {
    return {
      results: [
        {'name': 'a1','content': 'a2', 'isEdit': false,'change': false},
        {'name': 'a11','content': 'a22','isEdit': false,'change': false},
        {'name': 'a111','content': 'a222','isEdit': false,'change': false},
        {'name': 'a1111','content': 'a2222','isEdit': false,'change': false}
      ],
      datas: [],
      show: false,
      name: '',
      content: '',
      con:{
        'name': 'a1111','content': 'a2222','isEdit': false,'change': {'name': 'a1111','content': 'a2222','isEdit': false,'change': false}
      }
    }
  },

  components: {
    hel
  },
  methods: {
    add () {
      this.datas.push({'name': '','content': '','isEdit': true,'change': false})
    },
    save () {
      this.datas.forEach(element => {
        element.change = true
      });
      this.datas = this.datas.filter(element => {
          return element.name != '' && element.content != ''
      })
      console.log(this.datas)
    },
    del (index) {
      this.datas.splice(index, 1)
    },
    change () {
      this.datas.forEach(element => {
        element.change = false
      });

    }
  }
  // methods: {
  //    handleClick: function () {
  //               //按钮单击，count自增
  //               this.count++;
  //           },
  //    handleFileChange (e) {

  //       var self=this;
  //       var fileInput=e.target;
  //       if(fileInput.files.length==0){
  //           return;
  //       }
  //       this.upload()
  //   },

  // },
  // created() {
  //   let that = this
  //   this.$nextTick(() => {
  //       that.$refs.hello.innerHTML = '<span>sp</span>'
  //       that.$refs.helstyle.hello()
  //       console.log(that.$refs.helstyle.hes)
  //       // that.focus()
  //   })

  // }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
li{
  display: block;
  list-style: none;

}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
[v-clock]{

}
</style>
