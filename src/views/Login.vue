<!-- eslint-disable vue/multi-word-component-names -->
<!-- eslint-disable vue/valid-template-root -->
<template>
  <el-row class="login_top">
    <el-col :lg="16" :md="12" class="le-cols">欢迎光临</el-col>
    <el-col
      :lg="8"
      :md="12"
      class="le-cole"
      style="display: flex; justify-content: center; align-items: center"
    >
      <div class="cole">
        <h1>欢迎回来</h1>
        <div class="cole_spans">
          <s style="color: #dadddc">&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;</s>
          <span style="color: #dadddc">账号密码登录</span>
          <s style="color: #dadddc">&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;</s>
        </div>
        <el-form
          ref="ruleFormRef"
          :model="ruleForm"
          :rules="rules"
          class="demo-ruleForm"
          :size="formSize"
          status-icon
        >
          <el-form-item prop="username">
            <el-input v-model="ruleForm.username" placeholder="请输入用户名">
              <template #prefix>
                <el-icon class="el-input__icon"><User /></el-icon>
              </template>
            </el-input>
          </el-form-item>
          <el-form-item prop="password">
            <el-input v-model="ruleForm.password" placeholder="请输入密码">
              <template #prefix>
                <el-icon class="el-input__icon"><Lock /></el-icon>
              </template>
            </el-input>
          </el-form-item>
          <el-form-item>
            <el-button @click="submitForm(ruleFormRef)"> 登录 </el-button>
          </el-form-item>
        </el-form>
      </div>
    </el-col>
  </el-row>
</template>

<script lang="ts" setup>
import { reactive, ref } from 'vue';
import type { FormInstance, FormRules } from 'element-plus';

const formSize = ref('default');
const ruleFormRef = ref<FormInstance>();
const ruleForm = reactive({
  username: '',
  password: ''
});

const rules = reactive<FormRules>({
  username: [
    { required: true, message: '请输入用户', trigger: 'blur' },
    { min: 5, max: 8, message: '请输入正确格式', trigger: 'blur' }
  ],
  password: [
    { required: true, message: '请输入密码', trigger: 'blur' },
    { min: 5, max: 5, message: '请输入正确格式', trigger: 'blur' }
  ]
});

const submitForm = async (formEl: FormInstance | undefined) => {
  if (!formEl) return;
  await formEl.validate((valid, fields) => {
    if (valid) {
      console.log('submit!');
    } else {
      console.log('error submit!', fields);
    }
  });
};

const options = Array.from({ length: 10000 }).map((_, idx) => ({
  value: `${idx + 1}`,
  label: `${idx + 1}`
}));
</script>

<style lang="scss">
.login_top {
  width: 100%;
  height: 100vh;
}
.le-cols {
  width: 100%;
  height: 100%;
  background-color: #5c6df2;
  color: #fff;
  font-size: 22px;
  font-weight: 600;
  text-align: center;
  line-height: 100vh;
}
.le-cole {
  width: 100%;
  height: 100%;
}
.cole {
  width: 400px;
  height: 400px;
  text-align: center;
  padding: 15px;
  h1 {
    margin-top: 50px;
    margin-bottom: 15px;
  }
  s {
    margin: 5px;
  }
  .demo-ruleForm {
    margin-top: 20px;
  }
  .el-button {
    width: 100%;
    border-radius: 20px;
    background-color: #6071f2;
    color: #fff;
  }
}
</style>
<!--  -->
