<!--
 * @Author : vshow
 * @Date   : 2021-07-16 17:32
 * @WeChat : i-vshow
 * @Email  : vshow@dooomi.com
 * @Blog   : http://dooomi.com
-->

<template>
  <a-form-model ref="form" :model="form" :rules="rules">
    <a-form-model-item label="name" prop="user">
      <a-input v-model="form.user" placeholder="username">
        <a-icon slot="prefix" type="user" style="color: rgba(0, 0, 0, 0.25)" />
      </a-input>
    </a-form-model-item>
    <a-form-model-item label="password" prop="password">
      <a-input v-model="form.password" placeholder="Password">
        <a-icon slot="prefix" type="lock" style="color: rgba(0, 0, 0, 0.25)" />
      </a-input>
    </a-form-model-item>
  </a-form-model>
</template>

<script>
const defaultForm = {
  user: '',
  password: ''
};

export default {
  props: ['value'],
  data() {
    return {
      form: Object.assign({}, defaultForm, this.value),
      rules: {
        user: [{ required: true, message: 'Please input Activity name', trigger: 'blur' }],
        password: [{ required: true, message: 'Please input Activity password', trigger: 'blur' }]
      }
    };
  },
  methods: {
    submit() {
      return new Promise(resolve => this.$refs.form.validate(valid => valid && resolve(this.$attrs.model)));
    }
  }
};
</script>
