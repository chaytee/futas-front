<template>
  <div class="login-form">
    <div class="btn__wrap">
      <button class="btn__grade modal-show" @click="modalShow">ログイン</button>
    </div>
    <transition name="modal">
      <div class="modal is-active" v-if="isShow">
        <div class="modal-background" @click="modalClose"></div>
        <div class="modal-content">
          <div class="box p-4">
            <h2 class="welcome_title cen mb-5">ログイン</h2>
            <div class="error cen">{{ error }}</div>
            <form @submit.prevent="login" class="form__box">
              <div class="control has-icons-left">
                <input
                  class="input mb-4 is-medium"
                  type="email"
                  required
                  placeholder="メールアドレス"
                  v-model="email"
                />
                <span class="icon is-medium is-left">
                  <font-awesome-icon icon="envelope" />
                </span>
              </div>
              <div class="control has-icons-left">
                <input
                  class="input mb-4 is-medium"
                  type="password"
                  required
                  placeholder="パスワード"
                  v-model="password"
                />
                <span class="icon is-medium is-left">
                  <font-awesome-icon icon="key" />
                </span>
              </div>
              <div class="control has-icons-left">
                <input
                  class="input mb-4 is-medium"
                  type="password"
                  required
                  placeholder="パスワード（確認用）"
                  v-model="passwordConfirmation"
                />
                <span class="icon is-medium is-left">
                  <font-awesome-icon icon="key" />
                </span>
              </div>
              <div class="error">{{ error }}</div>
              <div class="btn__wrap">
                <button class="btn__grade" type="submit">ログインする</button>
              </div>
            </form>
          </div>
        </div>
        <button class="modal-close" @click="modalClose">×</button>
      </div>
    </transition>
  </div>
</template>
<script>
export default {
  emits: ["redirectToRelationship"],

  data() {
    return {
      email: "",
      password: "",
      isShow: false,
      passwordConfirmation: "",
      error: null,
    };
  },
  methods: {
    modalShow() {
      this.isShow = true;
    },
    modalClose() {
      this.isShow = false;
    },
    async login() {
      this.error = null;
      //キャッシュが残るため
      localStorage.clear();

      await this.$auth
        .loginWith("local", {
          data: {
            password: this.password,
            email: this.email,
          },
        })
        .then(
          (res) => {
            // レスポンスで返ってきた、認証に必要な情報をlocalStorageに保存
            window.localStorage.setItem("name", res.data.data.name);

            if(!res.data.data.relationship_id){
              this.$router.push("/relationship");
            }

            return res;
          },
          (error) => {
            this.error = error.response.data.errors;

            console.log(error.response.data.errors.full_messages);
            this.error = "ログインできませんでした";
            return;
          }
        );
    },
  },
};
</script>
