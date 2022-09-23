<template>
  <div class="wrapper">
    <div class="banner"></div>
    <div class="login">
      <div class="login-wrapper">
        <div class="login-title">
          <h2>Log In</h2>
        </div>
        <div class="login-form">
          <login-input>
            <template #icon>
              <icon icon-name="icon-touxiang"/>
            </template>
            <template #input>
              <input v-focus type="text" placeholder="User Name" v-model="name">
            </template>
          </login-input>
          <div class="passwd">

            <login-input
                v-show="!isShow"
                type="password"
                placeholder="Enter the password"
                v-model="passwd"
            >
              <template #icon>
                <icon icon-name="icon-jiesuo"/>
              </template>
            </login-input>
            <login-input
                v-show="isShow"
                placeholder="Enter the password"
                v-model="passwd"
            >
              <template #icon>
                <icon icon-name="icon-jiesuo"/>
              </template>
            </login-input>
            <div class="eye" @click="show">
              <icon v-if="!isShow" icon-name="icon-biyan"/>
              <icon v-if="isShow" icon-name="icon-yanjing"/>
            </div>
          </div>
          <div class="forget-passwd">
            <p>
              <a href="javascript:">Forget?</a>
            </p>
          </div>
          <div class="submit" @click="login">
            <label for="">
              <input type="submit" value="Login">
            </label>
          </div>
          <div class="register">
            <p>
              <a href="javascript:">Create account</a>
            </p>
          </div>
        </div>
        <div class="other">
          <icon icon-name="icon-QQ"/>
          <icon icon-name="icon-weixin"/>
          <icon icon-name="icon-youxiang"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import LoginInput from "@/components/loginInput/LoginInput";
import Icon from "@/components/icon/Icon";

export default {
  name: "Login",
  data() {
    return {
      isShow: false, // See the password
      name: '',
      passwd: "",
    }
  },
  methods: {
    login() {
      alert("Login success！")
    },
    // See the password
    show() {
      this.isShow = !this.isShow;
    }
  },
  components: {
    LoginInput,
    Icon,
  }
}
</script>

<style lang="scss" scoped>
.wrapper {
  width: 100%;
  height: 100vh;
}

.banner {
  width: 100%;
  height: 100%;
  background: url("~@/assets/banner.jpg") no-repeat {
    size: cover;
  };
}

.passwd {
  position: relative;

  .eye {
    position: absolute;
    top: 50%;
    right: 10px;
    transform: translateY(-50%);
  }
}

.login {
  position: absolute;
  top: 100px;
  right: 15%;
  width: 400px;
  padding-bottom: 40px;
  //height: 540px;
  border-radius: 3px;
  box-shadow: 0 4px 10px 0 rgba(0, 0, 0, .3);
  text-align: center;
  background: #fff;
}


.login-title {
  padding: 36px 0 25px;
  color: #21293a;
  font-size: 16px;
  line-height: 28px;
  text-align: center;
}

.login-form {
  width: 86%;
  margin: 0 auto;


  .forget-passwd, .register {
    text-align: right;

    a {
      font-size: 12px;
      color: #3B78DD;
    }
  }

  .register {
    margin-top: 12px;
  }

  .submit {
    overflow: hidden;
    height: 50px;
    line-height: 50px;
    margin-top: 14px;
    border-radius: 3px;
    background: #477EFF;

    label {
      border: none;
    }

    input {
      width: 100%;
      padding: 0;
      font-size: 16px;
      font-weight: 100;
      border-radius: 3px;
      text-align: center;
      color: #fff;
      border: none;
      background: none;
    }
  }


  .eye {
    z-index: 9999;
    position: absolute;
    top: 50%;
    right: 4px;
    transform: translateY(-50%);
    padding: 8px;
  }
}

.other {
  margin-top: 20px;

  span {
    display: inline-block;
    font-size: 40px;

    &:nth-child(2) {
      margin: 0 20px;
    }
  }
}
</style>