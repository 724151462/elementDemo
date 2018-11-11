<template>
    <el-row>
        <button @click="open">修改</button>
        <button @click="open1">添加</button>
        <Dialog 
            :formData="formData"
            :show.sync="show"></Dialog>
    </el-row>
    
</template>
<script>
import Dialog from '@/components/Dialog'
export default {
    data() {
        return{
            formData:[{
                key: '姓名：',
                inputType: 'string',
                value: ''
            },
            {
                key: '性别：',
                inputType: 'radio',
                option: ['男', '女'],
                value: ''
            },
            {
                key: '班级：',
                inputType: 'select',
                option: [{id: '1', label: '1班'}, {id:'2', label: '2班'}],
                value: ''
            }],
            mockData: ['wjx', '女', '2'],
            show: false
        }
    },
    created(){
        console.log(this)
    },
    methods: {
        open () {
            for(let i = 0; i<this.formData.length; i++){
                this.formData[i].value = this.mockData[i]
            }
            this.show = true;
        },
        open1 () {
            this.formData.forEach((item)=>{
                item.value = ''
            })
            console.log(this.formData)
            this.show = true;
        }
    },
    components:{
        Dialog
    }
}
</script>

