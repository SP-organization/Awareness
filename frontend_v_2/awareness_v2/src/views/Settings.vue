<template>
  <div class="container col-xxl-8 px-2 py-2 bg-white">
    <div class="row flex-lg-row align-items-center g-0 py-5">
      <div class="col-10 col-sm-8 col-lg-4 mb-3 mx-auto px-4 py-4 d-flex justify-content-center">
      </div>
      <div class="col-lg-8">
        <h1 class="display-5 lh-1 mb-3 ms-3"> {{ nickname }} </h1>
      </div>
    </div>

    <div class="container-fluid pb-3">
      <div class="d-flex align-items-start">
        <div class="mt-2 nav ps-2 flex-column nav-pills me-3"
             aria-orientation="vertical">
          <a class="nav-link btn btn-lg remove-glow"
             aria-selected="false">
            <router-link class="a" to="/diary">Мои дневники</router-link>
          </a>
          <a class="w-100 btn btn-lg btn-secondary text-light"
             aria-selected="true">
            <router-link class="a" to="/settings">Настройки</router-link>
          </a>
        </div>
        <div class="d-flex flex-column flex-grow-1 ms-5">
          <div class="mb-3">
            <h1 class="display-5">{{ 'Смена пароля' }}</h1>
            <form method="post">
              <div class="mb-3">
                <label for="InputOldPassword" class="form-label">{{ 'Старый пароль' }}</label>
                <input type="password" name="old_password" minlength="8"
                       class="form-control remove-glow" id="InputOldPassword"
                       required>
              </div>
              <div class="mb-3">
                <label for="InputNewPassword" class="form-label">{{ 'Новый пароль' }}</label>
                <input type="password" name="new_password" minlength="8"
                       class="form-control remove-glow" id="InputNewPassword"
                       required>
              </div>
              <button type="submit" name="password-change"
                      class="btn btn-lg btn-secondary text-light remove-glow">{{ 'Подтвердить' }}
              </button>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Settings",
  data() {
    return {
      nickname: '',
      errorMsg: `An error occurred, please try again`
    }
  },
  async created() {
    // GET request using axios with async/await// исправить в зависисмости от url
    const response = await axios.get("http://127.0.0.1:8000/edit_account");
    this.nickname = response.data["username"];
  },
}
</script>

<style scoped>

</style>