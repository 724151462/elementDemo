<template>
  <div id="test">
    单位：
    <select v-model="UnitSelected">
        <option v-for="item in UnitList" :value="item.id">{{item.name}}</option>
    </select>
    部门：
    <select v-model="DepartmentSelected">
        <option v-for="item in DepartmentList" :value="item.id">{{item.name}}</option>
    </select>
    用户：
    <select v-model="UserSelected">
        <option v-for="item in UserList" :value="item.id">{{item.name}}</option>
    </select>
    <router-link to='/a'>a</router-link>
    </div>
</template>

<script>
var UnitRows = [
    {name:"1",id:"1"},
    {name:"2",id:"2"},
];
var DepartmentRows = [
    {name:"11",id:"1",pid:"1"},
    {name:"12",id:"2",pid:"1"},
    {name:"21",id:"3",pid:"2"},
    {name:"22",id:"4",pid:"2"}
];
var UserRows = [
    {name:"111",id:"1",pid:"1"},
    {name:"112",id:"2",pid:"1"},
    {name:"121",id:"3",pid:"2"},
    {name:"122",id:"4",pid:"2"},
    {name:"211",id:"5",pid:"3"},
    {name:"212",id:"6",pid:"3"},
    {name:"221",id:"7",pid:"4"},
    {name:"222",id:"8",pid:"4"}
]
export default {
    data(){
        return{
            UnitSelected:"",
            UnitList:[],
            DepartmentSelected:"",
            DepartmentList:[],
            UserSelected:"",
            UserList:[]
        }
        
    },
    created:function () {
        console.log(this)
        this.UnitList = UnitRows
        this.UnitSelected = this.UnitList.length>0 ? this.UnitList[0].id : ''

        var val = this.UnitSelected;
        this.DepartmentList = DepartmentRows.filter(function(x) {return x.pid == val})
        this.DepartmentSelected = this.DepartmentList.length>0 ? this.DepartmentList[0].id : ''

        val = this.DepartmentSelected;
        this.UserList = UserRows.filter(function(x){return x.pid == val})
        this.UserSelected = this.UserList.length>0 ? this.UnitList[0].id : ''
    },
    watch:{
        UnitSelected:function (val) {
            this.DepartmentList = DepartmentRows.filter(function (x) { return x.pid == val });
            this.DepartmentSelected = this.DepartmentList.length>0 ? this.DepartmentList[0].id : "";
        },
        DepartmentSelected: function (val) {
            this.UserList = UserRows.filter(function(x){return x.id == val})
            this.UserSelected = this.UserList.length>0 ? this.UserList[0].id : ''
        }
    }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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
</style>
