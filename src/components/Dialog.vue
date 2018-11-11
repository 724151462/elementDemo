<template>
    <el-dialog
    title="title"
    :visible.sync="visible"
    @close="$emit('update:show', false)"
    width="30%">
    <el-form ref="form" :model="form" label-width="80px">
        <el-form-item v-for="(item, index) in formData" :key="index" :label="item.key">
            <el-input v-if="item.inputType=='string'" v-model="item.value"></el-input>
            <el-radio-group v-else-if="item.inputType=='radio'" v-model="item.value">
                <el-radio v-for="(val, i) in item.option" :key="i" :label="val"></el-radio>
            </el-radio-group>
            <el-select v-else-if="item.inputType=='select'" :label="item.key" v-model="item.value">
                <el-option v-for="(val, i) in item.option" :key="i" :label="val.label" :value="val.id"></el-option>
            </el-select>
        </el-form-item>
        </el-form-item>
        <!-- <el-form-item label="活动区域">
    <el-select v-model="form.region" placeholder="请选择活动区域">
      <el-option label="区域一" value="shanghai"></el-option>
      <el-option label="区域二" value="beijing"></el-option>
    </el-select>
  </el-form-item> -->
        <span slot="footer" class="dialog-footer">
            <el-button @click="visible = false">取 消</el-button>
            <el-button type="primary" @click="visible = false">确 定</el-button>
        </span>
        </el-form>
    </el-dialog>
</template>

<script>
export default {
    data () {
        return {
            visible: this.show,
            form: {
            }
        };
    },
    props: ['show', 'formData'],
    created(){
        console.log(this)
    },
    watch: {
        show () {
            this.visible = this.show;
        }
    }
}
</script>

<style>

</style>
