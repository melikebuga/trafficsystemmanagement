
<script setup lang="ts">
import { useHead } from '@vueuse/head'

import { useDarkmode } from '/@src/stores/darkmode'
import { useUserSession } from '/@src/stores/userSession'
// import { useNotyf } from '/@src/composable/useNotyf'
import sleep from '/@src/utils/sleep'

const isLoading = ref(false)
const darkmode = useDarkmode()
// const router = useRouter()
//const route = useRoute()
// const notif = useNotyf()
const userSession = useUserSession()
//const redirect = route.query.redirect as string

const handleLogin = async () => {
  if (!isLoading.value) {
    isLoading.value = true

    await sleep(2000)
    userSession.setToken('logged-in')

    // notif.dismissAll()
    // notif.success('Welcome back, Erik Kovalsky')

    // if (redirect) {
    //   router.push(redirect)
    // } else {
    //   router.push({
    //     name: '/liveTraffic',
    //   })
    // }
    window.location = '/liveTraffic'
    isLoading.value = false
  }
}

useHead({
  title: 'Auth Login - Vuero',
})
</script>

<template>
  <div class="auth-wrapper-inner columns is-gapless">
    <!-- Image section (hidden on mobile) -->
    <div class="column login-column is-8 h-hidden-mobile h-hidden-tablet-p hero-banner">
      <div class="hero login-hero is-fullheight is-app-grey">
        <div class="hero-body">
          <div class="columns">
            <div class="column is-10 is-offset-1">
              <img
                class="light-image has-light-shadow has-light-border"
                src="/@src/assets/illustrations/apps/vuero-banking-light.webp"
                alt=""
              />
              <img
                class="dark-image has-light-shadow"
                src="/@src/assets/illustrations/apps/vuero-banking-dark.webp"
                alt=""
              />
            </div>
          </div>
        </div>
        <div class="hero-footer">
          <p class="has-text-centered"></p>
        </div>
      </div>
    </div>

    <!-- Form section -->
    <div class="column is-4">
      <div class="hero is-fullheight is-white">
        <div class="hero-heading">
          <label
            class="dark-mode ml-auto"
            tabindex="0"
            @keydown.space.prevent="(e) => (e.target as HTMLLabelElement).click()"
          >
            <input
              type="checkbox"
              :checked="!darkmode.isDark"
              @change="darkmode.onChange"
            />
            <span></span>
          </label>
          <div class="auth-logo">
            <RouterLink to="/">
              <AnimatedLogo width="36px" height="36px" />
            </RouterLink>
          </div>
        </div>
        <div class="hero-body">
          <div class="container">
            <div class="columns">
              <div class="column is-12">
                <div class="auth-content">
                  <h2>Hoşgeldiniz</h2>
                </div>
                <div class="auth-form-wrapper">
                  <!-- Login Form -->
                  <form @submit.prevent="handleLogin">
                    <div class="login-form">
                      <!-- Username -->
                      <VField>
                        <VControl icon="feather:user">
                          <VInput
                            type="text"
                            placeholder="Kullanıcı Adı"
                            autocomplete="username"
                          />
                        </VControl>
                      </VField>

                      <!-- Password -->
                      <VField>
                        <VControl icon="feather:lock">
                          <VInput
                            type="password"
                            placeholder="Şifre"
                            autocomplete="current-password"
                          />
                        </VControl>
                      </VField>

                      <!-- Switch -->
                      <VField>
                        <VControl class="setting-item">
                          <VCheckbox label="Beni Hatırla" paddingless />
                        </VControl>
                      </VField>

                      <!-- Submit -->
                      <div class="login">
                        <VButton
                          :loading="isLoading"
                          color="primary"
                          type="submit"
                          bold
                          fullwidth
                          raised
                        >
                          GİRİŞ
                        </VButton>
                      </div>
                    </div>
                  </form>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.auth-wrapper-inner {
  overflow: hidden !important;
  height: 100%;
  padding: 0;
  margin: 0;

  &.is-gapless:not(:last-child) {
    margin-bottom: 0 !important;
  }

  &.is-single {
    background: var(--widget-grey);
    min-height: 100vh;
  }

  .hero-banner {
    background: var(--widget-grey);
  }

  .hero-heading {
    position: relative;
    max-width: 360px;
    width: 100%;
    margin: 0 auto;
    padding: 20px 0 0;

    .dark-mode {
      position: absolute;
      top: 24px;
      right: 24px;
      transform: scale(0.6);
      z-index: 2;
    }

    .auth-logo {
      display: flex;
      justify-content: center;

      svg {
        height: 42px;
        width: 42px;
      }

      .top-logo {
        height: 42px;
      }
    }
  }

  .hero {
    &.is-white {
      background: var(--white);
    }

    .hero-body {
      .login {
        padding: 10px 0;
      }

      .auth-content {
        max-width: 320px;
        width: 100%;
        margin: 0 auto;
        margin-top: -40px;
        margin-bottom: 40px;

        h2 {
          font-size: 2rem;
          font-family: var(--font);
          line-height: 1;
        }

        p {
          font-size: 1rem;
          margin-bottom: 8px;
          color: var(--muted-grey);
        }

        a {
          font-size: 0.9rem;
          font-family: var(--font-alt);
          font-weight: 500;
          color: var(--primary);
        }
      }

      .auth-form-wrapper {
        max-width: 320px;
        width: 100%;
        margin: 0 auto;
      }
    }
  }

  .forgot-link {
    margin-top: 10px;

    a {
      font-family: var(--font-alt);
      font-size: 0.9rem;
      color: var(--light-text);
      transition: color 0.3s;

      &:hover,
      &:focus {
        color: var(--primary);
      }
    }
  }

  .setting-item {
    display: flex;
    align-items: center;
    padding: 10px 0;

    .setting-meta {
      font-family: var(--font);
      color: var(--light-text);
      margin-left: 8px;
    }
  }

  .v-button {
    min-height: 44px;
  }
}

.is-dark {
  .auth-wrapper-inner {
    .hero-banner {
      background: var(--dark-sidebar-light-4);
    }

    .hero {
      &.is-white {
        background: var(--dark-sidebar-dark-4);
      }

      .hero-body {
        .auth-content {
          h2 {
            color: var(--dark-dark-text);
          }

          a {
            color: var(--primary);
          }
        }
      }
    }

    .forgot-link {
      a:hover {
        color: var(--primary);
      }
    }
  }
}

.auth-nav {
  position: absolute;
  top: 0;
  left: 0;
  height: 80px;
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;

  .left,
  .right {
    display: flex;
    align-items: center;
    width: 20%;
  }

  .right {
    justify-content: flex-end;

    .dark-mode {
      transform: scale(0.7);
    }
  }

  .center {
    flex-grow: 2;

    a {
      display: flex;
      justify-content: center;
      align-items: center;

      img {
        display: block;
        width: 100%;
        max-width: 50px;
      }
    }
  }
}

.auth-wrapper-inner {
  .single-form-wrap {
    min-height: 690px;
    padding: 0 16px;
    display: flex;
    align-items: center;
    justify-content: center;

    .inner-wrap {
      width: 100%;
      max-width: 400px;
      margin: 40px auto 0;

      .auth-head {
        max-width: 320px;
        width: 100%;
        margin: 0 auto;
        margin-bottom: 20px;
        text-align: center;

        h2 {
          font-size: 2rem;
          font-family: var(--font);
          line-height: 1;
        }

        p {
          font-size: 1rem;
          margin-bottom: 8px;
          color: var(--muted-grey);
        }

        a {
          font-size: 0.9rem;
          font-family: var(--font-alt);
          font-weight: 500;
          color: var(--primary);
        }
      }

      .form-card {
        background: var(--white);
        border: 1px solid var(--fade-grey-dark-3);
        border-radius: 10px;
        padding: 50px;
        margin-bottom: 16px;

        .v-button {
          margin-top: 10px;
        }
      }
    }
  }
}

.is-dark {
  .auth-wrapper-inner {
    &.is-single {
      background: var(--dark-sidebar-light-4);

      .single-form-wrap {
        .inner-wrap {
          .auth-head {
            h2 {
              color: var(--dark-dark-text);
            }

            a {
              color: var(--primary);
            }
          }

          .form-card {
            background: var(--dark-sidebar-dark-4);
            border-color: var(--dark-sidebar-light-1);
          }
        }
      }
    }
  }
}

@media only screen and (max-width: 767px) {
  .avatar-carousel {
    &.resized-mobile {
      max-width: 300px;
    }

    .slick-custom {
      display: none !important;
    }

    .image-wrapper img {
      height: auto;
    }
  }

  .auth-wrapper-inner {
    .hero {
      .hero-body {
        .auth-content {
          text-align: center !important;
        }
      }
    }

    .single-form-wrap {
      .inner-wrap {
        .form-card {
          padding: 40px;
        }
      }
    }
  }
}

@media only screen and (min-width: 768px) and (max-width: 1024px) and (orientation: portrait) {
  .modern-login {
    .top-logo {
      svg {
        height: 60px;
        width: 60px;
      }
    }

    .dark-mode {
      top: -58px;
      right: 30%;
    }

    .columns {
      display: flex;
      height: 100vh;
    }
  }

  .auth-wrapper-inner {
    .hero {
      .hero-body {
        .auth-content {
          text-align: center !important;
        }
      }
    }
  }

  .signup-columns {
    max-width: 460px;
    margin: 0 auto;
  }
}
</style>
