<template>
  <v-app>
    <div class="absolute appbar-intersect" style="top:0;left:0;right:0;height:65px;pointer-events:none;"
      data-v-18e8acf4=""></div>
    <v-app-bar :clipped-left="clipped" fixed app>
      <div class="container py-1 py-md-2" data-v-18e8acf4="">
        <div style="position:relative;" data-v-778fd3b9="" data-v-18e8acf4="">
          <div class="appbartop-grid" data-v-778fd3b9=""><a data-v-778fd3b9="" href="/"
              class="d-inline-block brand-logo align-self-center nuxt-link-active" style="line-height: 0;">
              <div class="d-inline-block" style="line-height: 0; margin: 0px 0px 0px -6px;"><img src="/img/logo.png"
                  alt="app-logo" height="42"></div>
            </a>
            <div class="d-flex justify-center mr-2 ml-sm-6 mr-sm-6" style="min-width: 0; min-height: 0;"
              data-v-778fd3b9="">
              <div class="w-full searchnav-width" data-v-c7897cd6="" data-v-778fd3b9=""><button type="button"
                  class="appsearchbar-btn v-btn v-btn--block v-btn--has-bg theme--light elevation-0 v-size--default"
                  style="height:40px;max-width:70%;" data-v-c7897cd6=""><span class="v-btn__content"><span
                      aria-hidden="true" class="v-icon notranslate mr-1 theme--light"
                      style="font-size:16px;height:16px;width:16px;" data-v-c7897cd6=""><svg
                        xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                        class="v-icon__svg" style="font-size:16px;height:16px;width:16px;">
                        <path
                          d="M9.5,3A6.5,6.5 0 0,1 16,9.5C16,11.11 15.41,12.59 14.44,13.73L14.71,14H15.5L20.5,19L19,20.5L14,15.5V14.71L13.73,14.44C12.59,15.41 11.11,16 9.5,16A6.5,6.5 0 0,1 3,9.5A6.5,6.5 0 0,1 9.5,3M9.5,5C7,5 5,7 5,9.5C5,12 7,14 9.5,14C12,14 14,12 14,9.5C14,7 12,5 9.5,5Z">
                        </path>
                      </svg></span> <span class="text-truncate" style="min-width:0;min-height:0;" data-v-c7897cd6="">
                      Fairmont Jakarta
                    </span> <span data-v-c7897cd6="">
                      &nbsp;&nbsp;·&nbsp;&nbsp;4 – 8 Mar 2025
                    </span></span></button> <!----></div>
            </div>
            <div data-v-778fd3b9=""><button type="button"
                class="v-btn v-btn--has-bg theme--light elevation-0 v-size--default primary"><span
                  class="v-btn__content">
                  Sign in
                </span></button> <!----></div>
          </div>
        </div>
      </div>
    </v-app-bar>

    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>

    <!--<v-footer :absolute="!fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>-->
    <footer class="d-print-none grey lighten-4" data-v-233ac83e="" data-v-18e8acf4="">
      <div class="container" data-v-233ac83e=""><!---->
        <div class="mt-3 d-flex align-center pb-3" data-v-233ac83e="">
          <div class="text-no-wrap" data-v-233ac83e=""><span class="text-body-2" data-v-233ac83e="">©</span>&nbsp;Wisata
            App
          </div> <span class="mx-3" data-v-233ac83e="">·</span> <a href="/termsandcondition" target="_blank"
            label="Terms" class="link text-h8 text--secondary" data-v-233ac83e="">
            Terms
          </a>
          <div class="spacer" data-v-233ac83e=""></div> <span class="text-button text-no-wrap" data-v-233ac83e="">
            v4.10
          </span>
        </div>
      </div>
    </footer>
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js'
    }
  }
}
</script>
