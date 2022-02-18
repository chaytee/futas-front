<template>
  <section id="welcome">
    <div class="hero__bg">
      <div class="hero__wrap">
        <div class="hero__in">
          <div class="hero__title cen">
            <img src="~/assets/img/title.png" alt="" />
          </div>
          <div class="box hero__box">
            <p class="cen">ようこそ！</p>
            <LoginForm @redirectToRelationship="redirectToRelationship" />
            <SignUp @redirectToRelationship="redirectToRelationship" />
          </div>
        </div>
        <div class="hero__img cen">
            <img src="~/assets/img/title_img.png" alt="" />
          </div>
      </div>
      <div class="item01 cen">
        <img src="~/assets/img/title_item01.png" alt="" />
      </div>
      <div class="item02 cen">
        <img src="~/assets/img/title_item02.png" alt="" />
      </div>
    </div>
  </section>
</template>

<script>
import LoginForm from "../components/LoginForm.vue";
import SignUp from "../components/SignUp.vue";

export default {
  layout: "welcomeType",
  components: { LoginForm, SignUp },
  data() {
    return {};
  },
  methods: {
    //認証コードが発行されていない場合は・・・に変更する
    redirectToRelationship() {
      this.$router.push("/relationship");
    },
  },
};
</script>

<style lang="scss">
#welcome {
  height: 100%;
  background-color: #fff;

  .hero__bg {
    box-sizing: border-box;
    position: relative;
    width: 100vw;
    height: 100%;
    top: 0;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    justify-content: center;
    align-items: flex-end;
    position: relative;

    &::before {
      content: "";
      width: 100%;
      height: 100%;
      position: absolute;
      top: 0;
      left: 0;
      z-index: 1;
      background: url(~@/assets/img/main_bg.jpg) no-repeat center top / cover;
    }
  }
  .item01 {
    position: absolute;
    top: 3%;
    left: 5%;
    z-index: 1;

    img {
      max-width: 180px;
    }
    @include ta {
      img {
        max-width: 120px;
      }
    }
    @include sm {
      img {
        max-width: 70px;
      }
    }
  }
  .item02 {
    position: absolute;
    top: 50px;
    right: 0;
    z-index: 1;
    img {
      max-width: 240px;
    }
    @include ta {
      top: 10%;

      img {
        max-width: 170px;
      }
    }
    @include sm {
      top: 12%;
      img {
        max-width: 100px;
      }
    }
  }
  .hero__wrap {
    height: 100%;
    box-sizing: border-box;
    margin: 0 auto;
    align-self: flex-end;
    position: relative;
    z-index: 2;

    @include hp {
      max-width: 1220px;
    }
    @include ta {
      margin: auto;
      align-self:auto;
    }
  }
  .hero__in {
    display: flex;
    justify-content: center;
    flex-flow: column;
    height: 100%;
  }
  .hero__title {
    margin-bottom: 20px;
    position: relative;
    z-index: 3;
    img {
      max-height: 150px;

      @include ta {
        max-height: 140px;
      }
      @include sm {
        padding: 0 10px;
      }
    }
  }
  .hero__img {
    position: absolute;
    bottom: 0;
    left: 0;
    z-index: 4;
  }
  .hero__box {
    width: 400px;
    margin: 0 auto;
    position: relative;
    z-index: 5;

    @include ta {
      width: 90%;
    }
  }

  .change-form {
    font-size: 14px;
    margin-top: 20px;
  }
  .form-link {
    color: rgba(244, 172, 172, 1);

    &:hover {
      opacity: 0.9;
      text-decoration: underline;
    }
  }
}
</style>
