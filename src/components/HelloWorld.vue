<!--  -->
<template>
    <div>
        <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
  <el-form-item label="患者姓名" prop="name">
    <el-input v-model="ruleForm.name"></el-input>
  </el-form-item>

  <el-form-item label="性别" prop="region">
    <el-select v-model="ruleForm.region" placeholder="请选择性别">
      <el-option label="男" value="shanghai"></el-option>
      <el-option label="女" value="beijing"></el-option>
      <el-option label="db" value="beijing"></el-option>
    </el-select>
  </el-form-item>

  <el-form-item label="身份证号" prop="idNumber">
    <el-input v-model="ruleForm.idNumber"></el-input>
  </el-form-item>

  <el-form-item label="发病时间" required>
    <el-col :span="11">
      <el-form-item prop="date1">
        <el-date-picker type="date" placeholder="选择日期" v-model="ruleForm.date1" style="width: 100%;"></el-date-picker>
      </el-form-item>
    </el-col>
    <el-col class="line" :span="2">-</el-col>
    <el-col :span="11">
      <el-form-item prop="date2">
        <el-time-picker placeholder="选择时间" v-model="ruleForm.date2" style="width: 100%;"></el-time-picker>
      </el-form-item>
    </el-col>
  </el-form-item>

  <el-form-item label="即时送医" prop="delivery">
    <el-switch v-model="ruleForm.delivery"></el-switch>
  </el-form-item>

  <el-form-item label="疾病性质" prop="type">
    <el-checkbox-group v-model="ruleForm.type">
      <el-checkbox label="db脑血栓" name="type"></el-checkbox>
      <el-checkbox label="fr大傻福" name="type"></el-checkbox>
      <el-checkbox label="wsl傻逼" name="type"></el-checkbox>
      <el-checkbox label="hw邋遢" name="type"></el-checkbox>
    </el-checkbox-group>
  </el-form-item>

  <el-form-item label="特殊病情" prop="resource">
    <el-radio-group v-model="ruleForm.resource">
      <el-radio label="已出现人传人现象！！！"></el-radio>
      <el-radio label="未出现人传人现象"></el-radio>
    </el-radio-group>
  </el-form-item>
  <el-form-item label="其他描述" prop="desc">
    <el-input type="textarea" v-model="ruleForm.desc"></el-input>
  </el-form-item>
  <el-form-item>
    <el-button type="primary" @click="submitForm('ruleForm')">提交</el-button>
    <el-button @click="resetForm('ruleForm')">重置</el-button>
  </el-form-item>
</el-form>
    </div>
</template>

<script>
  export default {
    name:'HelloWorld',
    data() {
      return {
        ruleForm: {
          name: '',
          region: '',
          date1: '',
          date2: '',
          delivery: false,
          type: [],
          resource: '',
          desc: '',
          idNumber:'',
        },
        rules: {
          name: [
            { required: true, message: '请输入姓名', trigger: 'blur' },
            { min: 1, max: 10, message: '长度在 1 到 10 个字符', trigger: 'blur' }
          ],
          idNumber:[
            { required: true, message: '请输入身份证号', trigger: 'blur' },
            { min: 3, max: 20, message: '长度在 3 到 20 个字符', trigger: 'blur' }
          ],
          region: [
            { required: true, message: '请选择性别', trigger: 'change' }
          ],
          date1: [
            { type: 'date', required: true, message: '请选择日期', trigger: 'change' }
          ],
          date2: [
            { type: 'date', required: true, message: '请选择时间', trigger: 'change' }
          ],
          type: [
            { type: 'array', required: true, message: '请至少选择一个活动性质', trigger: 'change' }
          ],
          resource: [
            { required: true, message: '请选择活动资源', trigger: 'change' }
          ],
          desc: [
            { required: true, message: '请填写活动形式', trigger: 'blur' }
          ]
        }
      };
    },
    methods: {
      submitForm(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            alert('卧槽你真填啊！没得救了 找块凉快地躺着吧');
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      },
      resetForm(formName) {
        this.$refs[formName].resetFields();
      }
    }
  }
</script>

<style lang='' scoped>

</style>