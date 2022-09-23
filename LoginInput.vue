<template>
  <div class="login-input">
    <label for="">
      <slot name="icon"></slot>
      <slot name="input">
        <input :type="type" :placeholder="placeholder" :value="value" @input="changeVal">
      </slot>
    </label>
  </div>
</template>

<script>
export default {
  name: "LoginInput",
  // props: ["value", "placeholder", "type"],
  props: {
    value: {

    },
    placeholder: {
      default: "请输入内容"
    },
    type: {
      default: "text"
    }
  },
  methods: {
    // 利用组件v-model传递value
    changeVal(e) {
      this.$emit("input", e.target.value);
    }
  }
}
</script>

<style lang="scss" scoped>

.login-passwd {
  position: relative;
}

.visible-passwd {
  z-index: -1;
  position: absolute;
  top: 0;
  left: 0;
}

label {
  position: relative;
  display: flex;
  align-items: center;
  width: 100%;
  height: 48px;
  margin-bottom: 17px;
  border: 1px solid #DADADA;;
  border-radius: 2px;
  text-align: left;
  color: #9095A2;

  span {
    padding-left: 8px;
    font-size: 22px;
    vertical-align: middle;
  }

  input {
    width: 80%;
    height: 90%;
    padding-left: 8px;
    font-size: 14px;
    font-weight: 600;

    &::placeholder {
      font-weight: 100;
      color: #ccc;
    }
  }
}

</style>