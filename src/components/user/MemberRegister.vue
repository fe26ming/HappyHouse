<template>
  <b-container class="bv-example-row mt-3">
    <b-row>
      <b-col>
        <b-alert variant="secondary" show><h3>회원가입</h3></b-alert>
      </b-col>
    </b-row>
    <b-row>
      <b-col></b-col>
      <b-col cols="8">
        <b-card class="text-center mt-3" style="max-width: 40rem" align="left">
          <b-form @submit="onSubmit" class="text-left">
            <b-alert show variant="danger" v-if="isLoginError"
              >아이디 또는 비밀번호를 확인하세요.</b-alert
            >
            <b-form-group label="이름:" label-for="username">
              <b-form-input
                id="username"
                v-model="user.username"
                required
                placeholder="이름 입력...."
              ></b-form-input>
            </b-form-group>
            <b-form-group label="아이디:" label-for="userid">
              <b-form-input
                id="userid"
                v-model="user.userid"
                required
                placeholder="아이디 입력...."
              ></b-form-input>
              <b-button
                type="button"
                variant="secondary"
                class="m-1"
                @click="checkid"
                >ID 중복 검사</b-button
              >
            </b-form-group>
            <b-form-group label="비밀번호:" label-for="userpwd">
              <b-form-input
                type="password"
                id="userpwd"
                v-model="user.userpwd"
                required
                placeholder="비밀번호 입력...."
              ></b-form-input>
            </b-form-group>
            <b-form-group label="이메일:" label-for="useremail">
              <b-form-input
                type="mail"
                id="useremail"
                v-model="user.useremail"
                required
                placeholder="이메일 입력...."
              ></b-form-input>
            </b-form-group>
            <b-form-group label="휴대폰 번호:" label-for="userphone">
              <b-form-input
                type="text"
                id="userphone"
                v-model="user.userphone"
                required
                placeholder="휴대폰 입력...."
              ></b-form-input>
            </b-form-group>
            <b-button type="submit" variant="primary" class="m-1"
              >회원가입</b-button
            >
          </b-form>
        </b-card>
      </b-col>
      <b-col></b-col
    ></b-row>
  </b-container>
</template>

<script>
import http from "@/api/http";

export default {
  name: "MemberLogin",
  data() {
    return {
      isLoginError: false,
      user: {
        username: "",
        userid: "",
        userpwd: "",
        useremail: "",
        userphone: "",
      },
    };
  },
  methods: {
    onSubmit(event) {
      event.preventDefault();

      let err = true;
      let msg = "";
      !this.user.userid &&
        ((msg = "ID 입력해주세요"), (err = false), this.$refs.userid.focus());
      err &&
        !this.user.userpwd &&
        ((msg = "비번 입력해주세요"),
        (err = false),
        this.$refs.userpwd.focus());

      if (!err) alert(msg);
      else this.registerMember();
    },
    registerMember() {
      http
        .post("/member", {
          name: this.user.username,
          id: this.user.userid,
          pw: this.user.userpwd,
          email: this.user.useremail,
          phone: this.user.userphone,
          prefer: null,
          emailAuthYn: false,
          emailAuthKey: null,
        })
        .then(({ data }) => {
          let msg = "회원 가입 실패.";
          if (data === "success") {
            msg = "회원 가입 완료.";
          }
          alert(msg);
          this.moveHome();
        });
    },
    movePage() {
      this.$router.push({ name: "SignUp" });
    },
    checkid() {
      alert("아이디 중복 체크!!");
    },
    moveHome() {
      this.$router.push({ name: "home" });
    },
  },
};
</script>

<style></style>
