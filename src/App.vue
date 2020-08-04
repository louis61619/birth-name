<template>
  <div id="app">
    <!-- 輸入資料 -->
    <h4>{{name}}</h4>
    <input type="text" placeholder="輸入姓名" v-model="name" />
    <h4>{{value}}</h4>
    <calender @childByValue="childByValue"></calender>
    <button @click="submit">送出資料</button>
    <br />
    <br />
    <!-- 表單 -->
    <table>
      <tr>
        <td>姓名</td>
        <td>生日</td>
        <td>年齡</td>
      </tr>
      <tr v-for="item in Arr" :key="item.index">
        <td>{{item.feildName}}</td>
        <td>{{item.feildBith}}</td>
        <td>{{item.feildAge}}</td>
      </tr>
    </table>
    <button @click="gofilter">放入資料</button>
    <br />
    <br />
    <!-- 月份 -->
    <table class="tab">
      <tr>
        <td>1月</td>
      </tr>
      <tr v-for="item in one" :key="item.index">
        <td>{{item.feildName}}</td>
      </tr>
    </table>

    <table class="tab">
      <tr>
        <td>2月</td>
      </tr>
      <tr v-for="item in two" :key="item.index">
        <td>{{item.feildName}}</td>
      </tr>
    </table>

    <table class="tab">
      <tr>
        <td>3月</td>
      </tr>
      <tr v-for="item in three" :key="item.index">
        <td>{{item.feildName}}</td>
      </tr>
    </table>

    <table class="tab">
      <tr>
        <td>4月</td>
      </tr>
      <tr v-for="item in four" :key="item.index">
        <td>{{item.feildName}}</td>
      </tr>
    </table>

    <table class="tab">
      <tr>
        <td>5月</td>
      </tr>
      <tr v-for="item in five" :key="item.index">
        <td>{{item.feildName}}</td>
      </tr>
    </table>

    <table class="tab">
      <tr>
        <td>6月</td>
      </tr>
      <tr v-for="item in six" :key="item.index">
        <td>{{item.feildName}}</td>
      </tr>
    </table>

    <table class="tab">
      <tr>
        <td>7月</td>
      </tr>
      <tr v-for="item in seven" :key="item.index">
        <td>{{item.feildName}}</td>
      </tr>
    </table>

    <table class="tab">
      <tr>
        <td>8月</td>
      </tr>
      <tr v-for="item in eight" :key="item.index">
        <td>{{item.feildName}}</td>
      </tr>
    </table>

    <table class="tab">
      <tr>
        <td>9月</td>
      </tr>
      <tr v-for="item in nine" :key="item.index">
        <td>{{item.feildName}}</td>
      </tr>
    </table>

    <table class="tab">
      <tr>
        <td>10月</td>
      </tr>
      <tr v-for="item in ten" :key="item.index">
        <td>{{item.feildName}}</td>
      </tr>
    </table>

    <table class="tab">
      <tr>
        <td>11月</td>
      </tr>
      <tr v-for="item in eleven" :key="item.index">
        <td>{{item.feildName}}</td>
      </tr>
    </table>

    <table class="tab">
      <tr>
        <td>12月</td>
      </tr>
      <tr v-for="item in twelve" :key="item.index">
        <td>{{item.feildName}}</td>
      </tr>
    </table>
    
  </div>
</template>

<script>
import Calender from "./components/Calender";

export default {
  name: "App",
  data() {
    return {
      value: "點擊日曆輸入生日",
      name: "",
      teacherAge: "",
      feild: {
        feildName: "",
        feildBith: "",
        feildAge: "",
        feildMonth: "",
      },
      Arr: [],
      one: [],
      two: [],
      three: [],
      four: [],
      five: [],
      six: [],
      seven: [],
      eight: [],
      nine: [],
      ten: [],
      eleven: [],
      twelve: []
    };
  },
  components: {
    Calender,
  },
  methods: {
    childByValue(value) {
      this.value = value;
    },
    submit() {
      if (this.name == "" || this.value == "點擊日曆輸入生日" || this.value == "") {
        alert("不能有空值");
      } else {
        this.getAge();
        this.feild.feildName = this.name;
        this.feild.feildBith = this.value;
        this.feild.feildAge = this.teacherAge;
        this.feild.feildMonth = new Date(this.value).getMonth() + 1;
        // console.log(this.feild)
        // this.Arr.push(obj)
        const copy = Object.assign({}, this.feild); //複製物件
        this.Arr.push(copy);
        this.Arr.sort(function (a, b) {
          return a.feildAge - b.feildAge;
        });
      }
    },
    getAge() {
      let birthdays = new Date(this.value.replace(/-/g, "/"));
      let d = new Date();
      let age =
        d.getFullYear() -
        birthdays.getFullYear() -
        (d.getMonth() < birthdays.getMonth() ||
        (d.getMonth() == birthdays.getMonth() &&
          d.getDate() < birthdays.getDate())
          ? 1
          : 0);
      this.teacherAge = age;
    },
    gofilter() {
      // console.log(this.Arr)
      for(let i=0; i < this.Arr.length; i++){
        if(this.Arr[i].feildMonth == 1){
          this.one.push(this.Arr[i])
        }else if(this.Arr[i].feildMonth == 2){
          this.two.push(this.Arr[i])
        }else if(this.Arr[i].feildMonth == 3){
          this.three.push(this.Arr[i])
        }else if(this.Arr[i].feildMonth == 4){
          this.four.push(this.Arr[i])
        }else if(this.Arr[i].feildMonth == 5){
          this.five.push(this.Arr[i])
        }else if(this.Arr[i].feildMonth == 6){
          this.six.push(this.Arr[i])
        }else if(this.Arr[i].feildMonth == 7){
          this.seven.push(this.Arr[i])
        }else if(this.Arr[i].feildMonth == 8){
          this.eight.push(this.Arr[i])
        }else if(this.Arr[i].feildMonth == 9){
          this.nine.push(this.Arr[i])
        }else if(this.Arr[i].feildMonth == 10){
          this.ten.push(this.Arr[i])
        }else if(this.Arr[i].feildMonth == 11){
          this.eleven.push(this.Arr[i])
        }else if(this.Arr[i].feildMonth == 12){
          this.twelve.push(this.Arr[i])
        }

      }
      console.log(this.one)
      this.Arr = []

      // Array.prototype.groupBy = function (prop) {
      //   return this.reduce(function (groups, item) {
      //     const val = item[prop];
      //     groups[val] = groups[val] || [];
      //     groups[val].push(item);
      //     return groups;
      //   }, {});
      // };

      // // initiate your groupBy. Notice the recordset Cars and the field Make....
      // const groupByMake = this.Arr.groupBy("feildMonth");
      // console.log(groupByMake);
    },
  },
};
</script>

<style scoped>
#app {
  margin-left: 50px;
}
.tab {
  display: inline-block;
  vertical-align: top;
  margin-bottom: 10px;
  
}
tr {
  border: 1px solid green;
}
td {
  border: 1px solid blue;
  width: 100px;
  height: 50px;
  text-align: center;
  line-height: 50px;
}
</style>
