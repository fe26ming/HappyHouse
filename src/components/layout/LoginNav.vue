<template>
  <div id="loginDiv">
    <router-link to="/">
      <a
        href="#"
        style="
          color: #00ffbf;
          font-size: 30px;
          font-weight: bold;
          text-decoration-line: none;
        "
        >HAPPY HOUSE</a
      > </router-link
    >&nbsp; ID<input
      id="userid"
      v-model="user.userid"
      size="7"
      required
      @keyup.enter="confirm"
    />&nbsp; PW<input
      size="7"
      v-model="user.userpwd"
      id="pw"
      type="password"
    />&nbsp;
    <b-button id="loginBtn" class="btn btn-primary" @click="confirm"
      >로그인</b-button
    >
    &nbsp; &nbsp;
    <button class="btn btn-primary">
      <router-link :to="{ name: 'findpw' }" class="link"></router-link>
      비밀번호 찾기
    </button>
  </div>
</template>

<script>
export default {
  name: "LoginNav",
  data() {
    return {
      isLoginError: false,
      user: {
        userid: "",
        userpwd: "",
      },
    };
  },
  methods: {
    confirm() {
      alert(this.user.userid + " " + this.user.userpwd);
    },
  },
};
</script>

<style></style>
