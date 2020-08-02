<template>
  <div>
    <!-- label -->
    <label v-if="label">{{label}}</label>
    <slot></slot>
    <!-- 错误信息 -->
    <p class="error" v-if="error">{{error}}</p>
    <!-- <Ytest @childBtn="add"></Ytest> -->
  </div>
</template>

<script>
import Validator from "async-validator";
import Ytest from "@/components/form/Ytest.vue";
export default {
  components: {
    Ytest,
  },
  inject: ["form"],
  data() {
    return {
      error: "",
    };
  },
  props: {
    label: {
      type: String,
      default: "",
    },
    prop: String,
  },
  mounted() {
    this.$on("Yvalidate", () => {
      this.validate2();
    });
  },
  methods: {
    add() {
      console.log("我是测试子组件！");
    },
    validate2() {
      // 校验规则
      const rules = this.form.rules[this.prop];
      // 当前值
      const value = this.form.model[this.prop];

      // 创建一个校验器实例
      const validator = new Validator({ [this.prop]: rules });
      // 校验，返回Promise
      return validator.validate({ [this.prop]: value }, (errors) => {
        if (errors) {
          this.error = errors[0].message;
        } else {
          this.error = "";
        }
      });
    },
  },
};
</script>