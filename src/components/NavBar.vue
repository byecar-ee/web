<template>
  <nav class="nav">
    <div class="nav__brand">
      <router-link to="/" exact class="nav__brand-link link">Byecar</router-link>
    </div>
    <div class="nav__links">
      <router-link to="/report" class="nav__links-link link"><font-awesome-icon icon="flag" class="link-icon"/> {{$t('nav.report')}} </router-link>
      <router-link to="/donate" class="nav__links-link link"><font-awesome-icon icon="donate" class="link-icon"/> {{$t('nav.donate')}} </router-link>
      <router-link to="/mission" class="nav__links-link link"><font-awesome-icon icon="bullseye" class="link-icon"/> {{$t('nav.mission')}} </router-link>
      <select v-model="locale" class="nav__locale-switcher">
        <option value="en">EN</option>
        <option value="ru">RU</option>
      </select>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'NavBar',
  data () {
    return {
      locale: this.$i18n.locale
    }
  },
  watch: {
    'locale' () {
      this.$i18n.locale = this.locale
      sessionStorage.setItem('byeCarLocale', this.locale)
    }
  }
}
</script>

<style scoped lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Staatliches&display=swap');

a {
  color: black;
  text-decoration: none;
}

.nav {
  display: inline-flex;
  justify-content: space-between;
  width: 100%;
  padding: 10px 0;

  &__brand {
    margin-left: 5%;
    align-self: center;
    transition: all 0.6s;
    &:hover {
      transform: scale(1.3);
    }
    &-link {
      font-family: 'Staatliches', cursive;
      font-size: 17pt;
    }
  }

  &__links {
    margin-right: 5%;
    align-self: center;
    &-link {
      padding: 0 10px;
      font-size: 13pt;
    }
  }
}

.link {
  color: white;
  transition: all 0.45s ease-in-out;
  &-icon {
    transition: all 0.45s ease-in-out;
    padding-right: 5px;
  }
  &:hover {
    color: #2A4747;
    .link-icon {
      transform: scale(1.1);
      margin-right: 5px;
    }
  }
}

@media only screen and (max-width: 750px) {
  .nav {
    display: flex;
    flex-direction: column;
    justify-content: center;
    flex-wrap: wrap;
    &__brand {
      margin: 0 0 5px 0;
    }
    &__links {
      margin: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      &-link {
        margin-bottom: 5px;
      }
    }
    &__locale-switcher {
      width: 100px;
    }
  }
}
</style>
