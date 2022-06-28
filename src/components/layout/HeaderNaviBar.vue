<template>
  <div>
    <nav
      class="navbar navbar-expand-lg bg-secondary text-uppercase fixed-top"
      id="mainNav"
    >
      <div class="container">
        <login-nav />

        <button
          class="navbar-toggler text-uppercase font-weight-bold bg-primary text-white rounded"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarResponsive"
          aria-controls="navbarResponsive"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          Menu
          <i class="fas fa-bars"></i>
        </button>
        <div class="collapse navbar-collapse" id="navbarResponsive">
          <ul class="navbar-nav ms-auto">
            <li class="nav-item mx-0 mx-lg-1">
              <a class="nav-link py-3 px-0 px-lg-3 rounded" href="#portfolio"
                >Portfolio</a
              >
            </li>
            <b-nav-item href="#"
              ><router-link :to="{ name: 'house' }" class="link"
                ><b-icon icon="house-fill" font-scale="1.5"></b-icon>
                아파트</router-link
              ></b-nav-item
            >
            <b-nav-item href="#"
              ><router-link :to="{ name: 'signUp' }" class="link"
                ><b-icon icon="person-fill" font-scale="1.5"></b-icon>
                회원가입</router-link
              ></b-nav-item
            >
            <b-nav-item href="#"
              ><router-link :to="{ name: 'board' }" class="link"
                ><b-icon icon="clipboard" font-scale="1.5"></b-icon>
                게시판</router-link
              ></b-nav-item
            >
            <li class="nav-item mx-0 mx-lg-1">
              <a href=""></a>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
import LoginNav from "@/components/layout/LoginNav.vue";

export default {
  name: "HeaderNaviBar",
  components: { LoginNav },
};
</script>

<style></style>
