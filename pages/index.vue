<template>
  <div>
    <div>
      <div id="location-catalog" class="pt-0 pt-sm-4 pb-6 pb-sm-8">
        <v-row>
          <div id="hero-image" class="d-flex justify-center col col-4">
            <v-avatar style="height: 168px; min-width: 168px; width: 168px;">
              <img
                :alt="property.name"
                :src="property.catalog_data.hero_image"
                class="w-full h-full"
                style="object-fit: cover; object-position: 50% 50%;"
              />
            </v-avatar>
          </div>
          <div id="catalog-data" class="flex-grow-1 ml-n2 ml-sm-0 col">
            <div id="catalog-header-desktop">
              <h1 class="font-weight-medium pr-1 text-h4">
                {{ property.name }}
              </h1>
              <span>
                <div style="margin-left: -3px;">
                  <v-icon
                    v-for="n in 5"
                    :key="n"
                    :color="n <= Math.ceil(starRating) ? 'amber' : 'grey'"
                  >
                    {{ getStarIcon(n) }}
                  </v-icon>
                </div>
              </span>
            </div>
            <div id="catalog-body">
              <p class="mb-0 text--secondary py-1 text-body-2">
                {{ property.catalog_data.category }}
              </p>
              <p class="mb-0 pb-1 text-body-2">
                {{ property.catalog_data.address_full }} {{ property.catalog_data.postal_code }}
              </p>
            </div>
            <div id="review-desktop" aria-hidden="true" class="d-flex align-center py-1 text-body-2">
              <v-progress-circular 
                v-if="property.review_graph !== null"
                :value="property.review_graph.rating" 
                :color="property.review_graph.color" 
                :size="34"
                :rotate="-90"
              >
                {{ property.review_graph.rating }}
              </v-progress-circular>
              <div v-else>Loading...</div>
              <span class="pl-2">{{ property.review_graph.category }} ·&nbsp;</span>
              <span>{{ property.catalog_data.review_count }} reviews</span>
            </div>
          </div>
        </v-row>
      </div>
      <Tab :photos="property.image_list" :info="property.important_info_data" />
      <!--
      <div>
        <div id="tabs-row-desktop" class="row align-center justify-space-between">
          <div class="col col-12">
            <hr role="separator" aria-orientation="horizontal" class="v-divider theme--light"
              style="margin-bottom: -1px;">
            <div class="v-tabs tab-no-background v-tabs--centered theme--light">
              <div role="tablist"
                class="v-item-group theme--light v-slide-group v-tabs-bar v-tabs-bar--is-mobile primary--text transparent"
                style="height: 52px;" data-booted="true">
                <div class="v-slide-group__prev v-slide-group__prev--disabled"></div>
                <div class="v-slide-group__wrapper">
                  <div class="v-slide-group__content v-tabs-bar__content">
                    <div class="v-tabs-slider-wrapper" style="height: 2px; left: 166px; width: 90px;">
                      <div class="v-tabs-slider"></div>
                    </div>
                    <div class="d-flex">
                      <div class="pl-3"></div> <a
                        href="/stay/fairmont-jakarta-9000248394/?checkin=2025-03-04&amp;checkout=2025-03-08&amp;guest_per_room=2&amp;number_of_room=1"
                        class="v-tab--active v-tab tab-no-background" tabindex="0" aria-selected="true" role="tab"
                        aria-current="page"><span class="v-badge v-badge--inline theme--light"><span
                            aria-hidden="true" class="v-icon notranslate v-icon--left theme--light"
                            style="font-size: 18px; height: 18px; width: 18px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 18px; height: 18px; width: 18px;">
                              <path
                                d="M21.41 11.58L12.41 2.58A2 2 0 0 0 11 2H4A2 2 0 0 0 2 4V11A2 2 0 0 0 2.59 12.42L11.59 21.42A2 2 0 0 0 13 22A2 2 0 0 0 14.41 21.41L21.41 14.41A2 2 0 0 0 22 13A2 2 0 0 0 21.41 11.58M13 20L4 11V4H11L20 13M6.5 5A1.5 1.5 0 1 1 5 6.5A1.5 1.5 0 0 1 6.5 5Z">
                              </path>
                            </svg></span> <span class="text-button font-weight-medium">
                            Deals
                          </span><span class="v-badge__wrapper"><span aria-atomic="true" aria-label="Badge"
                              aria-live="polite" role="status" class="v-badge__badge primary"
                              style="display: none;"></span></span></span></a>
                      <div class="pr-3"></div>
                    </div>
                    <div class="d-flex">
                      <div class="pl-3"></div> <a
                        href="/stay/fairmont-jakarta-9000248394/photos?checkin=2025-03-04&amp;checkout=2025-03-08&amp;guest_per_room=2&amp;number_of_room=1"
                        class="v-tab tab-no-background" tabindex="0" aria-selected="false" role="tab"><span
                          class="v-badge v-badge--inline theme--light"><span
                            aria-hidden="true" class="v-icon notranslate v-icon--left theme--light"
                            style="font-size: 18px; height: 18px; width: 18px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 18px; height: 18px; width: 18px;">
                              <path
                                d="M10,4V8H14V4H10M16,4V8H20V4H16M16,10V14H20V10H16M16,16V20H20V16H16M14,20V16H10V20H14M8,20V16H4V20H8M8,14V10H4V14H8M8,8V4H4V8H8M10,14H14V10H10V14M4,2H20A2,2 0 0,1 22,4V20A2,2 0 0,1 20,22H4C2.92,22 2,21.1 2,20V4A2,2 0 0,1 4,2Z">
                              </path>
                            </svg></span> <span class="text-button font-weight-medium">
                            Photos
                          </span><span class="v-badge__wrapper"><span aria-atomic="true" aria-label="Badge"
                              aria-live="polite" role="status" class="v-badge__badge primary"
                              style="display: none;"></span></span></span></a>
                      <div class="pr-3"></div>
                    </div>
                    <div class="d-flex">
                      <div class="pl-3"></div> <a
                        href="/stay/fairmont-jakarta-9000248394/info?checkin=2025-03-04&amp;checkout=2025-03-08&amp;guest_per_room=2&amp;number_of_room=1"
                        class="v-tab tab-no-background" tabindex="0" aria-selected="false" role="tab"><span
                          class="v-badge v-badge--inline theme--light"><span
                            aria-hidden="true" class="v-icon notranslate v-icon--left theme--light"
                            style="font-size: 18px; height: 18px; width: 18px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 18px; height: 18px; width: 18px;">
                              <path
                                d="M11,9H13V7H11M12,20C7.59,20 4,16.41 4,12C4,7.59 7.59,4 12,4C16.41,4 20,7.59 20,12C20,16.41 16.41,20 12,20M12,2A10,10 0 0,0 2,12A10,10 0 0,0 12,22A10,10 0 0,0 22,12A10,10 0 0,0 12,2M11,17H13V11H11V17Z">
                              </path>
                            </svg></span> <span class="text-button font-weight-medium">
                            Info
                          </span><span class="v-badge__wrapper"><span aria-atomic="true" aria-label="Badge"
                              aria-live="polite" role="status" class="v-badge__badge primary"
                              style="display: none;"></span></span></span></a>
                      <div class="pr-3"></div>
                    </div>
                  </div>
                </div>
                <div class="v-slide-group__next v-slide-group__next--disabled"></div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="nuxtchild" data-v-d935b814="">
        <div class="mt-4 mt-sm-1 mb-0 mb-sm-8 info" data-v-d935b814="">
          <div data-v-d935b814=""
            class="gutters-0 gutters-md-1 pt-sm-2 px-4 px-md-0 d-flex flex-column flex-sm-row justify-start align-stretch justify-sm-center"
            style="gap: 12px;">
            <div data-v-d935b814="" class="d-flex align-center"><span data-v-d935b814="" aria-hidden="true"
                class="v-icon notranslate ml-n1 text--primary theme--light"
                style="font-size: 18px; height: 18px; width: 18px;"><svg xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                  style="font-size: 18px; height: 18px; width: 18px;">
                  <path
                    d="M15,19.88C15.04,20.18 14.94,20.5 14.71,20.71C14.32,21.1 13.69,21.1 13.3,20.71L9.29,16.7C9.06,16.47 8.96,16.16 9,15.87V10.75L4.21,4.62C3.87,4.19 3.95,3.56 4.38,3.22C4.57,3.08 4.78,3 5,3V3H19V3C19.22,3 19.43,3.08 19.62,3.22C20.05,3.56 20.13,4.19 19.79,4.62L15,10.75V19.88M7.04,5L11,10.06V15.58L13,17.58V10.05L16.96,5H7.04Z">
                  </path>
                </svg></span>
              <p data-v-d935b814="" class="mb-0 ml-1 text-h8 text-md-h7 font-weight-medium text-no-wrap">
                Filter rooms by
              </p>
            </div>
            <div data-v-6aca2996="" data-v-d935b814=""
              class="stay-availability-wfilters wfilters d-flex flex-column align-center"
              style="--wfilters-gutters: 16px;">
              <div data-v-6aca2996="" class="relative w-full d-flex align-center justify-center">
                <div data-v-6aca2996="" class="wfilters-btn-reset">
                  <div data-v-6aca2996="" class="wfilters-btn-reset-fade v-sheet theme--light" style="height: 32px;">
                  </div> <button data-v-6aca2996="" type="button"
                    class="px-0 rounded-pill v-btn v-btn--outlined theme--light v-size--default primary--text"
                    style="height: 32px;"><span class="v-btn__content"><span data-v-6aca2996=""
                        class="font-weight-regular">
                        Clear All
                      </span>
                      <div data-v-6aca2996=""
                        class="ml-2 mr-n1 d-flex justify-center align-center white--text rounded-circle v-sheet theme--light primary"
                        style="height: 18px; width: 18px;"><span data-v-6aca2996=""
                          class="text-button font-weight-bold">
                          0
                        </span></div>
                    </span></button>
                </div>
                <div data-v-6aca2996=""
                  class="swiper-container swiper-container-initialized swiper-container-horizontal">
                  <div data-v-6aca2996="" class="swiper-wrapper" style="transform: translate3d(0px, 0px, 0px);">
                    <div data-v-d935b814="" class="swiper-slide swiper-slide-active" data-v-6aca2996=""
                      style="margin-right: 8px;"><span
                        class="v-chip v-chip--clickable v-chip--no-color v-chip--outlined theme--light v-size--default"><span
                          class="v-chip__content"><span aria-hidden="true" class="v-icon notranslate mr-2 theme--light"
                            style="font-size: 16px; height: 16px; width: 16px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 16px; height: 16px; width: 16px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span> <span class="">
                            Free Breakfast
                          </span></span></span></div>
                    <div data-v-d935b814="" class="swiper-slide swiper-slide-next" data-v-6aca2996=""
                      style="margin-right: 8px;"><span
                        class="v-chip v-chip--clickable v-chip--no-color v-chip--outlined theme--light v-size--default"><span
                          class="v-chip__content"><span aria-hidden="true" class="v-icon notranslate mr-2 theme--light"
                            style="font-size: 16px; height: 16px; width: 16px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 16px; height: 16px; width: 16px;">
                              <path
                                d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                              </path>
                            </svg></span> <span class="">
                            Free Cancellation
                          </span></span></span></div>
                  </div>
                </div>
              </div>
            </div>
          </div> 
          <div data-v-d935b814="" class="gutters-0 d-sm-none mt-4 v-sheet theme--light rounded-0 grey lighten-4"
            style="height: 24px;"></div>
        </div> 
        <div data-v-15d6fcda="" data-v-d935b814="" elevation="0" class="bg-transparent mb-sm-8 mb-md-10">
          <div data-v-15d6fcda="" class="stay-offer-grid">
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-catalog gutters-0 gutters-sm-1 pa-4 v-sheet v-sheet--outlined theme--light"
              style="--sticky-top: 56px; --sticky-bg: #FFFFFF; max-width: unset !important;">
              <div data-v-15d6fcda="" class="d-flex justify-space-between align-sm-center">
                <div data-v-15d6fcda="" class="d-flex flex-nowrap align-start">
                  <div data-v-15d6fcda="" class="text-h5 font-weight-medium">
                    Fairmont, Room, 2 Double Beds
                  </div>
                </div> <button data-v-15d6fcda="" type="button"
                  class="my-sm-n1 mr-n1 ml-1 ml-sm-0 v-btn v-btn--rounded v-btn--text theme--light v-size--small primary--text"><span
                    class="v-btn__content"><span data-v-15d6fcda="" class="text-h8 font-weight-medium">
                      See details
                    </span></span></button>
              </div>
              <div data-v-15d6fcda="" class="d-inline-flex flex-wrap"><span data-v-15d6fcda="" class="pr-3"><span
                    data-v-15d6fcda="" aria-hidden="true" class="v-icon notranslate theme--light"
                    style="font-size: 18px; height: 18px; width: 18px;"><svg xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                      style="font-size: 18px; height: 18px; width: 18px;">
                      <path
                        d="M20 10V7A2 2 0 0 0 18 5H6A2 2 0 0 0 4 7V10A2 2 0 0 0 2 12V17H3.33L4 19H5L5.67 17H18.33L19 19H20L20.67 17H22V12A2 2 0 0 0 20 10M13 7H18V10H13M6 7H11V10H6M20 15H4V12H20Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">2 Double
                    Beds</span></span> <span data-v-15d6fcda="" class="pr-3"><span data-v-15d6fcda="" aria-hidden="true"
                    class="v-icon notranslate theme--light" style="font-size: 16px; height: 16px; width: 16px;"><svg
                      xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                      class="v-icon__svg" style="font-size: 16px; height: 16px; width: 16px;">
                      <path
                        d="M23,15H21V17H23V15M23,11H21V13H23V11M23,19H21V21C22,21 23,20 23,19M15,3H13V5H15V3M23,7H21V9H23V7M21,3V5H23C23,4 22,3 21,3M3,21H11V15H1V19A2,2 0 0,0 3,21M3,7H1V9H3V7M15,19H13V21H15V19M19,3H17V5H19V3M19,19H17V21H19V19M3,3C2,3 1,4 1,5H3V3M3,11H1V13H3V11M11,3H9V5H11V3M7,3H5V5H7V3Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">49 m<sup
                      data-v-15d6fcda="">2</sup></span></span> </div>
              <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                class="mx-n4 mt-4 mb-n4 d-sm-none v-divider theme--light" style="max-width: unset;">
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-images mx-n4 mx-sm-0 overflow-hidden v-sheet theme--light rounded-lg">
              <div data-v-1409cccc="" data-v-15d6fcda=""
                class="stay-availability-room-images stay-availability-room-images--grid" style="cursor: pointer;">
                <div data-v-1409cccc="" class="stay-availability-room-images__main-img grey lighten-4"
                  style="grid-area: main;">
                  <div data-v-1409cccc="" class="relative">
                    <div data-v-978962ea="" data-v-1409cccc=""
                      class="bg-transparent overflow-hidden v-sheet theme--light aspect-ratio"
                      style="height: 0px; max-width: 100%; width: 100%; padding-bottom: 66.6667%; line-height: 0;"><img
                        data-v-978962ea="" alt="Room"
                        src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/5408c18a_b.jpg"
                        class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                    <div data-v-1409cccc=""
                      class="v-btn-stay-see-all-room-images absolute d-flex justify-center align-center rounded info elevation-1 ma-4 ma-sm-3 ma-md-4 px-2 py-1">
                      <span data-v-1409cccc="" aria-hidden="true"
                        class="v-icon notranslate mr-1 text--primary theme--light"
                        style="font-size: 16px; height: 16px; width: 16px;"><svg xmlns="http://www.w3.org/2000/svg"
                          viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                          style="font-size: 16px; height: 16px; width: 16px;">
                          <path
                            d="M10,4V8H14V4H10M16,4V8H20V4H16M16,10V14H20V10H16M16,16V20H20V16H16M14,20V16H10V20H14M8,20V16H4V20H8M8,14V10H4V14H8M8,8V4H4V8H8M10,14H14V10H10V14M4,2H20A2,2 0 0,1 22,4V20A2,2 0 0,1 20,22H4C2.92,22 2,21.1 2,20V4A2,2 0 0,1 4,2Z">
                          </path>
                        </svg></span> <span data-v-1409cccc="" class="pr-1 text-button text--primary font-weight-medium"
                        style="line-height: 1 !important;">
                        See Photos
                      </span></div>
                  </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-1;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/7f96225b_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-2;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/1b8343d0_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-3;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Bathroom"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/5db049b2_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
              </div>
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-offer bg-transparent v-sheet v-sheet--outlined theme--light">
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--silverware-slashed v-icon--left theme--light"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1">Without breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          3,084,600
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 12,338,400
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--silverware-slashed v-icon--left theme--light"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1">Without breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          3,084,600
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 12,338,400
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--left theme--light success--text"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1 success--text">Free Breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          3,636,400
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 14,545,600
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--left theme--light success--text"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1 success--text">Free Breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          3,636,400
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 14,545,600
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div data-v-15d6fcda="">
            <div class="v-dialog__container"></div>
          </div>
        </div>
        <div data-v-d935b814="" class="gutters-0 d-sm-none v-sheet theme--light rounded-0 grey lighten-4"
          style="height: 24px;"></div> 
        <div data-v-15d6fcda="" data-v-d935b814="" elevation="0" class="bg-transparent mb-sm-8 mb-md-10">
          <div data-v-15d6fcda="" class="stay-offer-grid">
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-catalog gutters-0 gutters-sm-1 pa-4 v-sheet v-sheet--outlined theme--light"
              style="--sticky-top: 56px; --sticky-bg: #FFFFFF; max-width: unset !important;">
              <div data-v-15d6fcda="" class="d-flex justify-space-between align-sm-center">
                <div data-v-15d6fcda="" class="d-flex flex-nowrap align-start">
                  <div data-v-15d6fcda="" class="text-h5 font-weight-medium">
                    Fairmont, Room, 1 King Bed
                  </div>
                </div> <button data-v-15d6fcda="" type="button"
                  class="my-sm-n1 mr-n1 ml-1 ml-sm-0 v-btn v-btn--rounded v-btn--text theme--light v-size--small primary--text"><span
                    class="v-btn__content"><span data-v-15d6fcda="" class="text-h8 font-weight-medium">
                      See details
                    </span></span></button>
              </div>
              <div data-v-15d6fcda="" class="d-inline-flex flex-wrap"><span data-v-15d6fcda="" class="pr-3"><span
                    data-v-15d6fcda="" aria-hidden="true" class="v-icon notranslate theme--light"
                    style="font-size: 18px; height: 18px; width: 18px;"><svg xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                      style="font-size: 18px; height: 18px; width: 18px;">
                      <path
                        d="M20 10V7A2 2 0 0 0 18 5H6A2 2 0 0 0 4 7V10A2 2 0 0 0 2 12V17H3.33L4 19H5L5.67 17H18.33L19 19H20L20.67 17H22V12A2 2 0 0 0 20 10M13 7H18V10H13M6 7H11V10H6M20 15H4V12H20Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">1 King Bed</span></span>
                <span data-v-15d6fcda="" class="pr-3"><span data-v-15d6fcda="" aria-hidden="true"
                    class="v-icon notranslate theme--light" style="font-size: 16px; height: 16px; width: 16px;"><svg
                      xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                      class="v-icon__svg" style="font-size: 16px; height: 16px; width: 16px;">
                      <path
                        d="M23,15H21V17H23V15M23,11H21V13H23V11M23,19H21V21C22,21 23,20 23,19M15,3H13V5H15V3M23,7H21V9H23V7M21,3V5H23C23,4 22,3 21,3M3,21H11V15H1V19A2,2 0 0,0 3,21M3,7H1V9H3V7M15,19H13V21H15V19M19,3H17V5H19V3M19,19H17V21H19V19M3,3C2,3 1,4 1,5H3V3M3,11H1V13H3V11M11,3H9V5H11V3M7,3H5V5H7V3Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">49 m<sup
                      data-v-15d6fcda="">2</sup></span></span> </div>
              <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                class="mx-n4 mt-4 mb-n4 d-sm-none v-divider theme--light" style="max-width: unset;">
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-images mx-n4 mx-sm-0 overflow-hidden v-sheet theme--light rounded-lg">
              <div data-v-1409cccc="" data-v-15d6fcda=""
                class="stay-availability-room-images stay-availability-room-images--grid" style="cursor: pointer;">
                <div data-v-1409cccc="" class="stay-availability-room-images__main-img grey lighten-4"
                  style="grid-area: main;">
                  <div data-v-1409cccc="" class="relative">
                    <div data-v-978962ea="" data-v-1409cccc=""
                      class="bg-transparent overflow-hidden v-sheet theme--light aspect-ratio"
                      style="height: 0px; max-width: 100%; width: 100%; padding-bottom: 66.6667%; line-height: 0;"><img
                        data-v-978962ea="" alt="Room"
                        src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/c6ddc7ec_b.jpg"
                        class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                    <div data-v-1409cccc=""
                      class="v-btn-stay-see-all-room-images absolute d-flex justify-center align-center rounded info elevation-1 ma-4 ma-sm-3 ma-md-4 px-2 py-1">
                      <span data-v-1409cccc="" aria-hidden="true"
                        class="v-icon notranslate mr-1 text--primary theme--light"
                        style="font-size: 16px; height: 16px; width: 16px;"><svg xmlns="http://www.w3.org/2000/svg"
                          viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                          style="font-size: 16px; height: 16px; width: 16px;">
                          <path
                            d="M10,4V8H14V4H10M16,4V8H20V4H16M16,10V14H20V10H16M16,16V20H20V16H16M14,20V16H10V20H14M8,20V16H4V20H8M8,14V10H4V14H8M8,8V4H4V8H8M10,14H14V10H10V14M4,2H20A2,2 0 0,1 22,4V20A2,2 0 0,1 20,22H4C2.92,22 2,21.1 2,20V4A2,2 0 0,1 4,2Z">
                          </path>
                        </svg></span> <span data-v-1409cccc="" class="pr-1 text-button text--primary font-weight-medium"
                        style="line-height: 1 !important;">
                        See Photos
                      </span></div>
                  </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-1;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/7f96225b_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-2;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/c1bac9a3_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-3;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Bathroom"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/5db049b2_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
              </div>
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-offer bg-transparent v-sheet v-sheet--outlined theme--light">
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--silverware-slashed v-icon--left theme--light"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1">Without breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          3,084,600
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 12,338,400
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--left theme--light success--text"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1 success--text">Free Breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          3,636,400
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 14,545,600
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div data-v-15d6fcda="">
            <div class="v-dialog__container"></div>
          </div>
        </div>
        <div data-v-d935b814="" class="gutters-0 d-sm-none v-sheet theme--light rounded-0 grey lighten-4"
          style="height: 24px;"></div> 
        <div data-v-15d6fcda="" data-v-d935b814="" elevation="0" class="bg-transparent mb-sm-8 mb-md-10">
          <div data-v-15d6fcda="" class="stay-offer-grid">
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-catalog gutters-0 gutters-sm-1 pa-4 v-sheet v-sheet--outlined theme--light"
              style="--sticky-top: 56px; --sticky-bg: #FFFFFF; max-width: unset !important;">
              <div data-v-15d6fcda="" class="d-flex justify-space-between align-sm-center">
                <div data-v-15d6fcda="" class="d-flex flex-nowrap align-start">
                  <div data-v-15d6fcda="" class="text-h5 font-weight-medium">
                    Deluxe Room, 2 Double Beds
                  </div>
                </div> <button data-v-15d6fcda="" type="button"
                  class="my-sm-n1 mr-n1 ml-1 ml-sm-0 v-btn v-btn--rounded v-btn--text theme--light v-size--small primary--text"><span
                    class="v-btn__content"><span data-v-15d6fcda="" class="text-h8 font-weight-medium">
                      See details
                    </span></span></button>
              </div>
              <div data-v-15d6fcda="" class="d-inline-flex flex-wrap"><span data-v-15d6fcda="" class="pr-3"><span
                    data-v-15d6fcda="" aria-hidden="true" class="v-icon notranslate theme--light"
                    style="font-size: 18px; height: 18px; width: 18px;"><svg xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                      style="font-size: 18px; height: 18px; width: 18px;">
                      <path
                        d="M20 10V7A2 2 0 0 0 18 5H6A2 2 0 0 0 4 7V10A2 2 0 0 0 2 12V17H3.33L4 19H5L5.67 17H18.33L19 19H20L20.67 17H22V12A2 2 0 0 0 20 10M13 7H18V10H13M6 7H11V10H6M20 15H4V12H20Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">2 Double
                    Beds</span></span> <span data-v-15d6fcda="" class="pr-3"><span data-v-15d6fcda="" aria-hidden="true"
                    class="v-icon notranslate theme--light" style="font-size: 16px; height: 16px; width: 16px;"><svg
                      xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                      class="v-icon__svg" style="font-size: 16px; height: 16px; width: 16px;">
                      <path
                        d="M23,15H21V17H23V15M23,11H21V13H23V11M23,19H21V21C22,21 23,20 23,19M15,3H13V5H15V3M23,7H21V9H23V7M21,3V5H23C23,4 22,3 21,3M3,21H11V15H1V19A2,2 0 0,0 3,21M3,7H1V9H3V7M15,19H13V21H15V19M19,3H17V5H19V3M19,19H17V21H19V19M3,3C2,3 1,4 1,5H3V3M3,11H1V13H3V11M11,3H9V5H11V3M7,3H5V5H7V3Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">69 m<sup
                      data-v-15d6fcda="">2</sup></span></span> </div>
              <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                class="mx-n4 mt-4 mb-n4 d-sm-none v-divider theme--light" style="max-width: unset;">
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-images mx-n4 mx-sm-0 overflow-hidden v-sheet theme--light rounded-lg">
              <div data-v-1409cccc="" data-v-15d6fcda=""
                class="stay-availability-room-images stay-availability-room-images--grid" style="cursor: pointer;">
                <div data-v-1409cccc="" class="stay-availability-room-images__main-img grey lighten-4"
                  style="grid-area: main;">
                  <div data-v-1409cccc="" class="relative">
                    <div data-v-978962ea="" data-v-1409cccc=""
                      class="bg-transparent overflow-hidden v-sheet theme--light aspect-ratio"
                      style="height: 0px; max-width: 100%; width: 100%; padding-bottom: 66.6667%; line-height: 0;"><img
                        data-v-978962ea="" alt="Room"
                        src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/5408c18a_b.jpg"
                        class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                    <div data-v-1409cccc=""
                      class="v-btn-stay-see-all-room-images absolute d-flex justify-center align-center rounded info elevation-1 ma-4 ma-sm-3 ma-md-4 px-2 py-1">
                      <span data-v-1409cccc="" aria-hidden="true"
                        class="v-icon notranslate mr-1 text--primary theme--light"
                        style="font-size: 16px; height: 16px; width: 16px;"><svg xmlns="http://www.w3.org/2000/svg"
                          viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                          style="font-size: 16px; height: 16px; width: 16px;">
                          <path
                            d="M10,4V8H14V4H10M16,4V8H20V4H16M16,10V14H20V10H16M16,16V20H20V16H16M14,20V16H10V20H14M8,20V16H4V20H8M8,14V10H4V14H8M8,8V4H4V8H8M10,14H14V10H10V14M4,2H20A2,2 0 0,1 22,4V20A2,2 0 0,1 20,22H4C2.92,22 2,21.1 2,20V4A2,2 0 0,1 4,2Z">
                          </path>
                        </svg></span> <span data-v-1409cccc="" class="pr-1 text-button text--primary font-weight-medium"
                        style="line-height: 1 !important;">
                        See Photos
                      </span></div>
                  </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-1;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/7f96225b_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-2;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/1b8343d0_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-3;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/66709555_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
              </div>
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-offer bg-transparent v-sheet v-sheet--outlined theme--light">
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--silverware-slashed v-icon--left theme--light"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1">Without breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          3,536,400
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 14,145,600
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--left theme--light success--text"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1 success--text">Free Breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          4,088,200
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 16,352,800
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div data-v-15d6fcda="">
            <div class="v-dialog__container"></div>
          </div>
        </div>
        <div data-v-d935b814="" class="gutters-0 d-sm-none v-sheet theme--light rounded-0 grey lighten-4"
          style="height: 24px;"></div> 
        <div data-v-15d6fcda="" data-v-d935b814="" elevation="0" class="bg-transparent mb-sm-8 mb-md-10">
          <div data-v-15d6fcda="" class="stay-offer-grid">
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-catalog gutters-0 gutters-sm-1 pa-4 v-sheet v-sheet--outlined theme--light"
              style="--sticky-top: 56px; --sticky-bg: #FFFFFF; max-width: unset !important;">
              <div data-v-15d6fcda="" class="d-flex justify-space-between align-sm-center">
                <div data-v-15d6fcda="" class="d-flex flex-nowrap align-start">
                  <div data-v-15d6fcda="" class="text-h5 font-weight-medium">
                    Fairmont Gold, Room, 2 Queen Beds
                  </div>
                </div> <button data-v-15d6fcda="" type="button"
                  class="my-sm-n1 mr-n1 ml-1 ml-sm-0 v-btn v-btn--rounded v-btn--text theme--light v-size--small primary--text"><span
                    class="v-btn__content"><span data-v-15d6fcda="" class="text-h8 font-weight-medium">
                      See details
                    </span></span></button>
              </div>
              <div data-v-15d6fcda="" class="d-inline-flex flex-wrap"><span data-v-15d6fcda="" class="pr-3"><span
                    data-v-15d6fcda="" aria-hidden="true" class="v-icon notranslate theme--light"
                    style="font-size: 18px; height: 18px; width: 18px;"><svg xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                      style="font-size: 18px; height: 18px; width: 18px;">
                      <path
                        d="M20 10V7A2 2 0 0 0 18 5H6A2 2 0 0 0 4 7V10A2 2 0 0 0 2 12V17H3.33L4 19H5L5.67 17H18.33L19 19H20L20.67 17H22V12A2 2 0 0 0 20 10M13 7H18V10H13M6 7H11V10H6M20 15H4V12H20Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">2 Queen
                    Beds</span></span> <span data-v-15d6fcda="" class="pr-3"><span data-v-15d6fcda="" aria-hidden="true"
                    class="v-icon notranslate theme--light" style="font-size: 16px; height: 16px; width: 16px;"><svg
                      xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                      class="v-icon__svg" style="font-size: 16px; height: 16px; width: 16px;">
                      <path
                        d="M23,15H21V17H23V15M23,11H21V13H23V11M23,19H21V21C22,21 23,20 23,19M15,3H13V5H15V3M23,7H21V9H23V7M21,3V5H23C23,4 22,3 21,3M3,21H11V15H1V19A2,2 0 0,0 3,21M3,7H1V9H3V7M15,19H13V21H15V19M19,3H17V5H19V3M19,19H17V21H19V19M3,3C2,3 1,4 1,5H3V3M3,11H1V13H3V11M11,3H9V5H11V3M7,3H5V5H7V3Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">49 m<sup
                      data-v-15d6fcda="">2</sup></span></span> </div>
              <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                class="mx-n4 mt-4 mb-n4 d-sm-none v-divider theme--light" style="max-width: unset;">
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-images mx-n4 mx-sm-0 overflow-hidden v-sheet theme--light rounded-lg">
              <div data-v-1409cccc="" data-v-15d6fcda=""
                class="stay-availability-room-images stay-availability-room-images--grid" style="cursor: pointer;">
                <div data-v-1409cccc="" class="stay-availability-room-images__main-img grey lighten-4"
                  style="grid-area: main;">
                  <div data-v-1409cccc="" class="relative">
                    <div data-v-978962ea="" data-v-1409cccc=""
                      class="bg-transparent overflow-hidden v-sheet theme--light aspect-ratio"
                      style="height: 0px; max-width: 100%; width: 100%; padding-bottom: 66.6667%; line-height: 0;"><img
                        data-v-978962ea="" alt="Room"
                        src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/5408c18a_b.jpg"
                        class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                    <div data-v-1409cccc=""
                      class="v-btn-stay-see-all-room-images absolute d-flex justify-center align-center rounded info elevation-1 ma-4 ma-sm-3 ma-md-4 px-2 py-1">
                      <span data-v-1409cccc="" aria-hidden="true"
                        class="v-icon notranslate mr-1 text--primary theme--light"
                        style="font-size: 16px; height: 16px; width: 16px;"><svg xmlns="http://www.w3.org/2000/svg"
                          viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                          style="font-size: 16px; height: 16px; width: 16px;">
                          <path
                            d="M10,4V8H14V4H10M16,4V8H20V4H16M16,10V14H20V10H16M16,16V20H20V16H16M14,20V16H10V20H14M8,20V16H4V20H8M8,14V10H4V14H8M8,8V4H4V8H8M10,14H14V10H10V14M4,2H20A2,2 0 0,1 22,4V20A2,2 0 0,1 20,22H4C2.92,22 2,21.1 2,20V4A2,2 0 0,1 4,2Z">
                          </path>
                        </svg></span> <span data-v-1409cccc="" class="pr-1 text-button text--primary font-weight-medium"
                        style="line-height: 1 !important;">
                        See Photos
                      </span></div>
                  </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-1;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/7f96225b_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-2;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/096dfb7c_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-3;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/696f146a_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
              </div>
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-offer bg-transparent v-sheet v-sheet--outlined theme--light">
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--silverware-slashed v-icon--left theme--light"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1">Without breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          3,744,100
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 14,976,400
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--silverware-slashed v-icon--left theme--light"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1">Without breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          3,744,100
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 14,976,400
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--left theme--light success--text"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1 success--text">Free Breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          4,295,900
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 17,183,600
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--left theme--light success--text"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1 success--text">Free Breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          4,295,900
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 17,183,600
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div data-v-15d6fcda="">
            <div class="v-dialog__container"></div>
          </div>
        </div>
        <div data-v-d935b814="" class="gutters-0 d-sm-none v-sheet theme--light rounded-0 grey lighten-4"
          style="height: 24px;"></div> 
        <div data-v-15d6fcda="" data-v-d935b814="" elevation="0" class="bg-transparent mb-sm-8 mb-md-10">
          <div data-v-15d6fcda="" class="stay-offer-grid">
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-catalog gutters-0 gutters-sm-1 pa-4 v-sheet v-sheet--outlined theme--light"
              style="--sticky-top: 56px; --sticky-bg: #FFFFFF; max-width: unset !important;">
              <div data-v-15d6fcda="" class="d-flex justify-space-between align-sm-center">
                <div data-v-15d6fcda="" class="d-flex flex-nowrap align-start">
                  <div data-v-15d6fcda="" class="text-h5 font-weight-medium">
                    Fairmont Gold, Room, 1 King Bed
                  </div>
                </div> <button data-v-15d6fcda="" type="button"
                  class="my-sm-n1 mr-n1 ml-1 ml-sm-0 v-btn v-btn--rounded v-btn--text theme--light v-size--small primary--text"><span
                    class="v-btn__content"><span data-v-15d6fcda="" class="text-h8 font-weight-medium">
                      See details
                    </span></span></button>
              </div>
              <div data-v-15d6fcda="" class="d-inline-flex flex-wrap"><span data-v-15d6fcda="" class="pr-3"><span
                    data-v-15d6fcda="" aria-hidden="true" class="v-icon notranslate theme--light"
                    style="font-size: 18px; height: 18px; width: 18px;"><svg xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                      style="font-size: 18px; height: 18px; width: 18px;">
                      <path
                        d="M20 10V7A2 2 0 0 0 18 5H6A2 2 0 0 0 4 7V10A2 2 0 0 0 2 12V17H3.33L4 19H5L5.67 17H18.33L19 19H20L20.67 17H22V12A2 2 0 0 0 20 10M13 7H18V10H13M6 7H11V10H6M20 15H4V12H20Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">1 King Bed</span></span>
                <span data-v-15d6fcda="" class="pr-3"><span data-v-15d6fcda="" aria-hidden="true"
                    class="v-icon notranslate theme--light" style="font-size: 16px; height: 16px; width: 16px;"><svg
                      xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                      class="v-icon__svg" style="font-size: 16px; height: 16px; width: 16px;">
                      <path
                        d="M23,15H21V17H23V15M23,11H21V13H23V11M23,19H21V21C22,21 23,20 23,19M15,3H13V5H15V3M23,7H21V9H23V7M21,3V5H23C23,4 22,3 21,3M3,21H11V15H1V19A2,2 0 0,0 3,21M3,7H1V9H3V7M15,19H13V21H15V19M19,3H17V5H19V3M19,19H17V21H19V19M3,3C2,3 1,4 1,5H3V3M3,11H1V13H3V11M11,3H9V5H11V3M7,3H5V5H7V3Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">49 m<sup
                      data-v-15d6fcda="">2</sup></span></span> </div>
              <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                class="mx-n4 mt-4 mb-n4 d-sm-none v-divider theme--light" style="max-width: unset;">
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-images mx-n4 mx-sm-0 overflow-hidden v-sheet theme--light rounded-lg">
              <div data-v-1409cccc="" data-v-15d6fcda=""
                class="stay-availability-room-images stay-availability-room-images--grid" style="cursor: pointer;">
                <div data-v-1409cccc="" class="stay-availability-room-images__main-img grey lighten-4"
                  style="grid-area: main;">
                  <div data-v-1409cccc="" class="relative">
                    <div data-v-978962ea="" data-v-1409cccc=""
                      class="bg-transparent overflow-hidden v-sheet theme--light aspect-ratio"
                      style="height: 0px; max-width: 100%; width: 100%; padding-bottom: 66.6667%; line-height: 0;"><img
                        data-v-978962ea="" alt="Room"
                        src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/c6ddc7ec_b.jpg"
                        class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                    <div data-v-1409cccc=""
                      class="v-btn-stay-see-all-room-images absolute d-flex justify-center align-center rounded info elevation-1 ma-4 ma-sm-3 ma-md-4 px-2 py-1">
                      <span data-v-1409cccc="" aria-hidden="true"
                        class="v-icon notranslate mr-1 text--primary theme--light"
                        style="font-size: 16px; height: 16px; width: 16px;"><svg xmlns="http://www.w3.org/2000/svg"
                          viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                          style="font-size: 16px; height: 16px; width: 16px;">
                          <path
                            d="M10,4V8H14V4H10M16,4V8H20V4H16M16,10V14H20V10H16M16,16V20H20V16H16M14,20V16H10V20H14M8,20V16H4V20H8M8,14V10H4V14H8M8,8V4H4V8H8M10,14H14V10H10V14M4,2H20A2,2 0 0,1 22,4V20A2,2 0 0,1 20,22H4C2.92,22 2,21.1 2,20V4A2,2 0 0,1 4,2Z">
                          </path>
                        </svg></span> <span data-v-1409cccc="" class="pr-1 text-button text--primary font-weight-medium"
                        style="line-height: 1 !important;">
                        See Photos
                      </span></div>
                  </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-1;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/7f96225b_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-2;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/c1bac9a3_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-3;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/73e0d399_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
              </div>
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-offer bg-transparent v-sheet v-sheet--outlined theme--light">
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--silverware-slashed v-icon--left theme--light"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1">Without breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          3,744,100
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 14,976,400
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--silverware-slashed v-icon--left theme--light"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1">Without breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          3,744,100
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 14,976,400
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--left theme--light success--text"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1 success--text">Free Breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          4,295,900
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 17,183,600
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--left theme--light success--text"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1 success--text">Free Breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          4,295,900
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 17,183,600
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div data-v-15d6fcda="">
            <div class="v-dialog__container"></div>
          </div>
        </div>
        <div data-v-d935b814="" class="gutters-0 d-sm-none v-sheet theme--light rounded-0 grey lighten-4"
          style="height: 24px;"></div> 
        <div data-v-15d6fcda="" data-v-d935b814="" elevation="0" class="bg-transparent mb-sm-8 mb-md-10">
          <div data-v-15d6fcda="" class="stay-offer-grid">
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-catalog gutters-0 gutters-sm-1 pa-4 v-sheet v-sheet--outlined theme--light"
              style="--sticky-top: 56px; --sticky-bg: #FFFFFF; max-width: unset !important;">
              <div data-v-15d6fcda="" class="d-flex justify-space-between align-sm-center">
                <div data-v-15d6fcda="" class="d-flex flex-nowrap align-start">
                  <div data-v-15d6fcda="" class="text-h5 font-weight-medium">
                    Fairmont Gold, Room, 2 Double Beds
                  </div>
                </div> <button data-v-15d6fcda="" type="button"
                  class="my-sm-n1 mr-n1 ml-1 ml-sm-0 v-btn v-btn--rounded v-btn--text theme--light v-size--small primary--text"><span
                    class="v-btn__content"><span data-v-15d6fcda="" class="text-h8 font-weight-medium">
                      See details
                    </span></span></button>
              </div>
              <div data-v-15d6fcda="" class="d-inline-flex flex-wrap"><span data-v-15d6fcda="" class="pr-3"><span
                    data-v-15d6fcda="" aria-hidden="true" class="v-icon notranslate theme--light"
                    style="font-size: 18px; height: 18px; width: 18px;"><svg xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                      style="font-size: 18px; height: 18px; width: 18px;">
                      <path
                        d="M20 10V7A2 2 0 0 0 18 5H6A2 2 0 0 0 4 7V10A2 2 0 0 0 2 12V17H3.33L4 19H5L5.67 17H18.33L19 19H20L20.67 17H22V12A2 2 0 0 0 20 10M13 7H18V10H13M6 7H11V10H6M20 15H4V12H20Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">2 Double
                    Beds</span></span> <span data-v-15d6fcda="" class="pr-3"><span data-v-15d6fcda="" aria-hidden="true"
                    class="v-icon notranslate theme--light" style="font-size: 16px; height: 16px; width: 16px;"><svg
                      xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                      class="v-icon__svg" style="font-size: 16px; height: 16px; width: 16px;">
                      <path
                        d="M23,15H21V17H23V15M23,11H21V13H23V11M23,19H21V21C22,21 23,20 23,19M15,3H13V5H15V3M23,7H21V9H23V7M21,3V5H23C23,4 22,3 21,3M3,21H11V15H1V19A2,2 0 0,0 3,21M3,7H1V9H3V7M15,19H13V21H15V19M19,3H17V5H19V3M19,19H17V21H19V19M3,3C2,3 1,4 1,5H3V3M3,11H1V13H3V11M11,3H9V5H11V3M7,3H5V5H7V3Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">49 m<sup
                      data-v-15d6fcda="">2</sup></span></span> </div>
              <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                class="mx-n4 mt-4 mb-n4 d-sm-none v-divider theme--light" style="max-width: unset;">
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-images mx-n4 mx-sm-0 overflow-hidden v-sheet theme--light rounded-lg">
              <div data-v-1409cccc="" data-v-15d6fcda=""
                class="stay-availability-room-images stay-availability-room-images--grid" style="cursor: pointer;">
                <div data-v-1409cccc="" class="stay-availability-room-images__main-img grey lighten-4"
                  style="grid-area: main;">
                  <div data-v-1409cccc="" class="relative">
                    <div data-v-978962ea="" data-v-1409cccc=""
                      class="bg-transparent overflow-hidden v-sheet theme--light aspect-ratio"
                      style="height: 0px; max-width: 100%; width: 100%; padding-bottom: 66.6667%; line-height: 0;"><img
                        data-v-978962ea="" alt="Room"
                        src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/5408c18a_b.jpg"
                        class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                    <div data-v-1409cccc=""
                      class="v-btn-stay-see-all-room-images absolute d-flex justify-center align-center rounded info elevation-1 ma-4 ma-sm-3 ma-md-4 px-2 py-1">
                      <span data-v-1409cccc="" aria-hidden="true"
                        class="v-icon notranslate mr-1 text--primary theme--light"
                        style="font-size: 16px; height: 16px; width: 16px;"><svg xmlns="http://www.w3.org/2000/svg"
                          viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                          style="font-size: 16px; height: 16px; width: 16px;">
                          <path
                            d="M10,4V8H14V4H10M16,4V8H20V4H16M16,10V14H20V10H16M16,16V20H20V16H16M14,20V16H10V20H14M8,20V16H4V20H8M8,14V10H4V14H8M8,8V4H4V8H8M10,14H14V10H10V14M4,2H20A2,2 0 0,1 22,4V20A2,2 0 0,1 20,22H4C2.92,22 2,21.1 2,20V4A2,2 0 0,1 4,2Z">
                          </path>
                        </svg></span> <span data-v-1409cccc="" class="pr-1 text-button text--primary font-weight-medium"
                        style="line-height: 1 !important;">
                        See Photos
                      </span></div>
                  </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-1;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/7f96225b_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-2;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/1b8343d0_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-3;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/73e0d399_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
              </div>
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-offer bg-transparent v-sheet v-sheet--outlined theme--light">
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--silverware-slashed v-icon--left theme--light"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1">Without breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          3,939,500
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 15,758,000
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--left theme--light success--text"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1 success--text">Free Breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          4,491,300
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 17,965,200
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div data-v-15d6fcda="">
            <div class="v-dialog__container"></div>
          </div>
        </div>
        <div data-v-d935b814="" class="gutters-0 d-sm-none v-sheet theme--light rounded-0 grey lighten-4"
          style="height: 24px;"></div> 
        <div data-v-15d6fcda="" data-v-d935b814="" elevation="0" class="bg-transparent mb-sm-8 mb-md-10">
          <div data-v-15d6fcda="" class="stay-offer-grid">
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-catalog gutters-0 gutters-sm-1 pa-4 v-sheet v-sheet--outlined theme--light"
              style="--sticky-top: 56px; --sticky-bg: #FFFFFF; max-width: unset !important;">
              <div data-v-15d6fcda="" class="d-flex justify-space-between align-sm-center">
                <div data-v-15d6fcda="" class="d-flex flex-nowrap align-start">
                  <div data-v-15d6fcda="" class="text-h5 font-weight-medium">
                    Room
                  </div>
                </div> <button data-v-15d6fcda="" type="button"
                  class="my-sm-n1 mr-n1 ml-1 ml-sm-0 v-btn v-btn--rounded v-btn--text theme--light v-size--small primary--text"><span
                    class="v-btn__content"><span data-v-15d6fcda="" class="text-h8 font-weight-medium">
                      See details
                    </span></span></button>
              </div>
              <div data-v-15d6fcda="" class="d-inline-flex flex-wrap"><span data-v-15d6fcda="" class="pr-3"><span
                    data-v-15d6fcda="" aria-hidden="true" class="v-icon notranslate theme--light"
                    style="font-size: 18px; height: 18px; width: 18px;"><svg xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                      style="font-size: 18px; height: 18px; width: 18px;">
                      <path
                        d="M20 10V7A2 2 0 0 0 18 5H6A2 2 0 0 0 4 7V10A2 2 0 0 0 2 12V17H3.33L4 19H5L5.67 17H18.33L19 19H20L20.67 17H22V12A2 2 0 0 0 20 10M13 7H18V10H13M6 7H11V10H6M20 15H4V12H20Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">1 King Bed</span></span>
                <span data-v-15d6fcda="" class="pr-3"><span data-v-15d6fcda="" aria-hidden="true"
                    class="v-icon notranslate theme--light" style="font-size: 16px; height: 16px; width: 16px;"><svg
                      xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                      class="v-icon__svg" style="font-size: 16px; height: 16px; width: 16px;">
                      <path
                        d="M23,15H21V17H23V15M23,11H21V13H23V11M23,19H21V21C22,21 23,20 23,19M15,3H13V5H15V3M23,7H21V9H23V7M21,3V5H23C23,4 22,3 21,3M3,21H11V15H1V19A2,2 0 0,0 3,21M3,7H1V9H3V7M15,19H13V21H15V19M19,3H17V5H19V3M19,19H17V21H19V19M3,3C2,3 1,4 1,5H3V3M3,11H1V13H3V11M11,3H9V5H11V3M7,3H5V5H7V3Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">65 m<sup
                      data-v-15d6fcda="">2</sup></span></span> </div>
              <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                class="mx-n4 mt-4 mb-n4 d-sm-none v-divider theme--light" style="max-width: unset;">
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-images mx-n4 mx-sm-0 overflow-hidden v-sheet theme--light rounded-lg">
              <div data-v-1409cccc="" data-v-15d6fcda=""
                class="stay-availability-room-images stay-availability-room-images--grid" style="cursor: pointer;">
                <div data-v-1409cccc="" class="stay-availability-room-images__main-img grey lighten-4"
                  style="grid-area: main;">
                  <div data-v-1409cccc="" class="relative">
                    <div data-v-978962ea="" data-v-1409cccc=""
                      class="bg-transparent overflow-hidden v-sheet theme--light aspect-ratio"
                      style="height: 0px; max-width: 100%; width: 100%; padding-bottom: 66.6667%; line-height: 0;"><img
                        data-v-978962ea="" alt="Room"
                        src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/c6ddc7ec_b.jpg"
                        class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                    <div data-v-1409cccc=""
                      class="v-btn-stay-see-all-room-images absolute d-flex justify-center align-center rounded info elevation-1 ma-4 ma-sm-3 ma-md-4 px-2 py-1">
                      <span data-v-1409cccc="" aria-hidden="true"
                        class="v-icon notranslate mr-1 text--primary theme--light"
                        style="font-size: 16px; height: 16px; width: 16px;"><svg xmlns="http://www.w3.org/2000/svg"
                          viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                          style="font-size: 16px; height: 16px; width: 16px;">
                          <path
                            d="M10,4V8H14V4H10M16,4V8H20V4H16M16,10V14H20V10H16M16,16V20H20V16H16M14,20V16H10V20H14M8,20V16H4V20H8M8,14V10H4V14H8M8,8V4H4V8H8M10,14H14V10H10V14M4,2H20A2,2 0 0,1 22,4V20A2,2 0 0,1 20,22H4C2.92,22 2,21.1 2,20V4A2,2 0 0,1 4,2Z">
                          </path>
                        </svg></span> <span data-v-1409cccc="" class="pr-1 text-button text--primary font-weight-medium"
                        style="line-height: 1 !important;">
                        See Photos
                      </span></div>
                  </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-1;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/7f96225b_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-2;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/c1bac9a3_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-3;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/096dfb7c_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
              </div>
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-offer bg-transparent v-sheet v-sheet--outlined theme--light">
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--silverware-slashed v-icon--left theme--light"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1">Without breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          4,122,700
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 16,490,800
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--left theme--light success--text"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1 success--text">Free Breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          4,674,400
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 18,697,600
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div data-v-15d6fcda="">
            <div class="v-dialog__container"></div>
          </div>
        </div>
        <div data-v-d935b814="" class="gutters-0 d-sm-none v-sheet theme--light rounded-0 grey lighten-4"
          style="height: 24px;"></div> 
        <div data-v-15d6fcda="" data-v-d935b814="" elevation="0" class="bg-transparent mb-sm-8 mb-md-10">
          <div data-v-15d6fcda="" class="stay-offer-grid">
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-catalog gutters-0 gutters-sm-1 pa-4 v-sheet v-sheet--outlined theme--light"
              style="--sticky-top: 56px; --sticky-bg: #FFFFFF; max-width: unset !important;">
              <div data-v-15d6fcda="" class="d-flex justify-space-between align-sm-center">
                <div data-v-15d6fcda="" class="d-flex flex-nowrap align-start">
                  <div data-v-15d6fcda="" class="text-h5 font-weight-medium">
                    Deluxe Room
                  </div>
                </div> <button data-v-15d6fcda="" type="button"
                  class="my-sm-n1 mr-n1 ml-1 ml-sm-0 v-btn v-btn--rounded v-btn--text theme--light v-size--small primary--text"><span
                    class="v-btn__content"><span data-v-15d6fcda="" class="text-h8 font-weight-medium">
                      See details
                    </span></span></button>
              </div>
              <div data-v-15d6fcda="" class="d-inline-flex flex-wrap"><span data-v-15d6fcda="" class="pr-3"><span
                    data-v-15d6fcda="" aria-hidden="true" class="v-icon notranslate theme--light"
                    style="font-size: 18px; height: 18px; width: 18px;"><svg xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                      style="font-size: 18px; height: 18px; width: 18px;">
                      <path
                        d="M20 10V7A2 2 0 0 0 18 5H6A2 2 0 0 0 4 7V10A2 2 0 0 0 2 12V17H3.33L4 19H5L5.67 17H18.33L19 19H20L20.67 17H22V12A2 2 0 0 0 20 10M13 7H18V10H13M6 7H11V10H6M20 15H4V12H20Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">1 King Bed</span></span>
                <span data-v-15d6fcda="" class="pr-3"><span data-v-15d6fcda="" aria-hidden="true"
                    class="v-icon notranslate theme--light" style="font-size: 16px; height: 16px; width: 16px;"><svg
                      xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                      class="v-icon__svg" style="font-size: 16px; height: 16px; width: 16px;">
                      <path
                        d="M23,15H21V17H23V15M23,11H21V13H23V11M23,19H21V21C22,21 23,20 23,19M15,3H13V5H15V3M23,7H21V9H23V7M21,3V5H23C23,4 22,3 21,3M3,21H11V15H1V19A2,2 0 0,0 3,21M3,7H1V9H3V7M15,19H13V21H15V19M19,3H17V5H19V3M19,19H17V21H19V19M3,3C2,3 1,4 1,5H3V3M3,11H1V13H3V11M11,3H9V5H11V3M7,3H5V5H7V3Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">65 m<sup
                      data-v-15d6fcda="">2</sup></span></span> </div>
              <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                class="mx-n4 mt-4 mb-n4 d-sm-none v-divider theme--light" style="max-width: unset;">
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-images mx-n4 mx-sm-0 overflow-hidden v-sheet theme--light rounded-lg">
              <div data-v-1409cccc="" data-v-15d6fcda=""
                class="stay-availability-room-images stay-availability-room-images--grid" style="cursor: pointer;">
                <div data-v-1409cccc="" class="stay-availability-room-images__main-img grey lighten-4"
                  style="grid-area: main;">
                  <div data-v-1409cccc="" class="relative">
                    <div data-v-978962ea="" data-v-1409cccc=""
                      class="bg-transparent overflow-hidden v-sheet theme--light aspect-ratio"
                      style="height: 0px; max-width: 100%; width: 100%; padding-bottom: 66.6667%; line-height: 0;"><img
                        data-v-978962ea="" alt="Room"
                        src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/c6ddc7ec_b.jpg"
                        class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                    <div data-v-1409cccc=""
                      class="v-btn-stay-see-all-room-images absolute d-flex justify-center align-center rounded info elevation-1 ma-4 ma-sm-3 ma-md-4 px-2 py-1">
                      <span data-v-1409cccc="" aria-hidden="true"
                        class="v-icon notranslate mr-1 text--primary theme--light"
                        style="font-size: 16px; height: 16px; width: 16px;"><svg xmlns="http://www.w3.org/2000/svg"
                          viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                          style="font-size: 16px; height: 16px; width: 16px;">
                          <path
                            d="M10,4V8H14V4H10M16,4V8H20V4H16M16,10V14H20V10H16M16,16V20H20V16H16M14,20V16H10V20H14M8,20V16H4V20H8M8,14V10H4V14H8M8,8V4H4V8H8M10,14H14V10H10V14M4,2H20A2,2 0 0,1 22,4V20A2,2 0 0,1 20,22H4C2.92,22 2,21.1 2,20V4A2,2 0 0,1 4,2Z">
                          </path>
                        </svg></span> <span data-v-1409cccc="" class="pr-1 text-button text--primary font-weight-medium"
                        style="line-height: 1 !important;">
                        See Photos
                      </span></div>
                  </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-1;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/7f96225b_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-2;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/c1bac9a3_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-3;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/096dfb7c_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
              </div>
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-offer bg-transparent v-sheet v-sheet--outlined theme--light">
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--silverware-slashed v-icon--left theme--light"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1">Without breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          4,318,100
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 17,272,400
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--left theme--light success--text"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1 success--text">Free Breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          4,869,800
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 19,479,200
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div data-v-15d6fcda="">
            <div class="v-dialog__container"></div>
          </div>
        </div>
        <div data-v-d935b814="" class="gutters-0 d-sm-none v-sheet theme--light rounded-0 grey lighten-4"
          style="height: 24px;"></div> 
        <div data-v-15d6fcda="" data-v-d935b814="" elevation="0" class="bg-transparent mb-sm-8 mb-md-10">
          <div data-v-15d6fcda="" class="stay-offer-grid">
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-catalog gutters-0 gutters-sm-1 pa-4 v-sheet v-sheet--outlined theme--light"
              style="--sticky-top: 56px; --sticky-bg: #FFFFFF; max-width: unset !important;">
              <div data-v-15d6fcda="" class="d-flex justify-space-between align-sm-center">
                <div data-v-15d6fcda="" class="d-flex flex-nowrap align-start">
                  <div data-v-15d6fcda="" class="text-h5 font-weight-medium">
                    Fairmont, Suite
                  </div>
                </div> <button data-v-15d6fcda="" type="button"
                  class="my-sm-n1 mr-n1 ml-1 ml-sm-0 v-btn v-btn--rounded v-btn--text theme--light v-size--small primary--text"><span
                    class="v-btn__content"><span data-v-15d6fcda="" class="text-h8 font-weight-medium">
                      See details
                    </span></span></button>
              </div>
              <div data-v-15d6fcda="" class="d-inline-flex flex-wrap"><span data-v-15d6fcda="" class="pr-3"><span
                    data-v-15d6fcda="" aria-hidden="true" class="v-icon notranslate theme--light"
                    style="font-size: 18px; height: 18px; width: 18px;"><svg xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                      style="font-size: 18px; height: 18px; width: 18px;">
                      <path
                        d="M20 10V7A2 2 0 0 0 18 5H6A2 2 0 0 0 4 7V10A2 2 0 0 0 2 12V17H3.33L4 19H5L5.67 17H18.33L19 19H20L20.67 17H22V12A2 2 0 0 0 20 10M13 7H18V10H13M6 7H11V10H6M20 15H4V12H20Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">1 King Bed</span></span>
                <span data-v-15d6fcda="" class="pr-3"><span data-v-15d6fcda="" aria-hidden="true"
                    class="v-icon notranslate theme--light" style="font-size: 16px; height: 16px; width: 16px;"><svg
                      xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                      class="v-icon__svg" style="font-size: 16px; height: 16px; width: 16px;">
                      <path
                        d="M23,15H21V17H23V15M23,11H21V13H23V11M23,19H21V21C22,21 23,20 23,19M15,3H13V5H15V3M23,7H21V9H23V7M21,3V5H23C23,4 22,3 21,3M3,21H11V15H1V19A2,2 0 0,0 3,21M3,7H1V9H3V7M15,19H13V21H15V19M19,3H17V5H19V3M19,19H17V21H19V19M3,3C2,3 1,4 1,5H3V3M3,11H1V13H3V11M11,3H9V5H11V3M7,3H5V5H7V3Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">113 m<sup
                      data-v-15d6fcda="">2</sup></span></span> </div>
              <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                class="mx-n4 mt-4 mb-n4 d-sm-none v-divider theme--light" style="max-width: unset;">
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-images mx-n4 mx-sm-0 overflow-hidden v-sheet theme--light rounded-lg">
              <div data-v-1409cccc="" data-v-15d6fcda=""
                class="stay-availability-room-images stay-availability-room-images--grid" style="cursor: pointer;">
                <div data-v-1409cccc="" class="stay-availability-room-images__main-img grey lighten-4"
                  style="grid-area: main;">
                  <div data-v-1409cccc="" class="relative">
                    <div data-v-978962ea="" data-v-1409cccc=""
                      class="bg-transparent overflow-hidden v-sheet theme--light aspect-ratio"
                      style="height: 0px; max-width: 100%; width: 100%; padding-bottom: 66.6667%; line-height: 0;"><img
                        data-v-978962ea="" alt="Room"
                        src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/496d1f42_b.jpg"
                        class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                    <div data-v-1409cccc=""
                      class="v-btn-stay-see-all-room-images absolute d-flex justify-center align-center rounded info elevation-1 ma-4 ma-sm-3 ma-md-4 px-2 py-1">
                      <span data-v-1409cccc="" aria-hidden="true"
                        class="v-icon notranslate mr-1 text--primary theme--light"
                        style="font-size: 16px; height: 16px; width: 16px;"><svg xmlns="http://www.w3.org/2000/svg"
                          viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                          style="font-size: 16px; height: 16px; width: 16px;">
                          <path
                            d="M10,4V8H14V4H10M16,4V8H20V4H16M16,10V14H20V10H16M16,16V20H20V16H16M14,20V16H10V20H14M8,20V16H4V20H8M8,14V10H4V14H8M8,8V4H4V8H8M10,14H14V10H10V14M4,2H20A2,2 0 0,1 22,4V20A2,2 0 0,1 20,22H4C2.92,22 2,21.1 2,20V4A2,2 0 0,1 4,2Z">
                          </path>
                        </svg></span> <span data-v-1409cccc="" class="pr-1 text-button text--primary font-weight-medium"
                        style="line-height: 1 !important;">
                        See Photos
                      </span></div>
                  </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-1;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/7f96225b_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-2;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/002087e1_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-3;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Bathroom"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/5db049b2_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
              </div>
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-offer bg-transparent v-sheet v-sheet--outlined theme--light">
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--silverware-slashed v-icon--left theme--light"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1">Without breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          4,611,300
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 18,445,200
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--left theme--light success--text"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1 success--text">Free Breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          5,163,000
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 20,652,000
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div data-v-15d6fcda="">
            <div class="v-dialog__container"></div>
          </div>
        </div>
        <div data-v-d935b814="" class="gutters-0 d-sm-none v-sheet theme--light rounded-0 grey lighten-4"
          style="height: 24px;"></div> 
        <div data-v-15d6fcda="" data-v-d935b814="" elevation="0" class="bg-transparent mb-sm-8 mb-md-10">
          <div data-v-15d6fcda="" class="stay-offer-grid">
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-catalog gutters-0 gutters-sm-1 pa-4 v-sheet v-sheet--outlined theme--light"
              style="--sticky-top: 56px; --sticky-bg: #FFFFFF; max-width: unset !important;">
              <div data-v-15d6fcda="" class="d-flex justify-space-between align-sm-center">
                <div data-v-15d6fcda="" class="d-flex flex-nowrap align-start">
                  <div data-v-15d6fcda="" class="text-h5 font-weight-medium">
                    Fairmont Gold King, Room
                  </div>
                </div> <button data-v-15d6fcda="" type="button"
                  class="my-sm-n1 mr-n1 ml-1 ml-sm-0 v-btn v-btn--rounded v-btn--text theme--light v-size--small primary--text"><span
                    class="v-btn__content"><span data-v-15d6fcda="" class="text-h8 font-weight-medium">
                      See details
                    </span></span></button>
              </div>
              <div data-v-15d6fcda="" class="d-inline-flex flex-wrap"><span data-v-15d6fcda="" class="pr-3"><span
                    data-v-15d6fcda="" aria-hidden="true" class="v-icon notranslate theme--light"
                    style="font-size: 18px; height: 18px; width: 18px;"><svg xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                      style="font-size: 18px; height: 18px; width: 18px;">
                      <path
                        d="M20 10V7A2 2 0 0 0 18 5H6A2 2 0 0 0 4 7V10A2 2 0 0 0 2 12V17H3.33L4 19H5L5.67 17H18.33L19 19H20L20.67 17H22V12A2 2 0 0 0 20 10M13 7H18V10H13M6 7H11V10H6M20 15H4V12H20Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">2 Double
                    Beds</span></span> <span data-v-15d6fcda="" class="pr-3"><span data-v-15d6fcda="" aria-hidden="true"
                    class="v-icon notranslate theme--light" style="font-size: 16px; height: 16px; width: 16px;"><svg
                      xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                      class="v-icon__svg" style="font-size: 16px; height: 16px; width: 16px;">
                      <path
                        d="M23,15H21V17H23V15M23,11H21V13H23V11M23,19H21V21C22,21 23,20 23,19M15,3H13V5H15V3M23,7H21V9H23V7M21,3V5H23C23,4 22,3 21,3M3,21H11V15H1V19A2,2 0 0,0 3,21M3,7H1V9H3V7M15,19H13V21H15V19M19,3H17V5H19V3M19,19H17V21H19V19M3,3C2,3 1,4 1,5H3V3M3,11H1V13H3V11M11,3H9V5H11V3M7,3H5V5H7V3Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">49 m<sup
                      data-v-15d6fcda="">2</sup></span></span> </div>
              <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                class="mx-n4 mt-4 mb-n4 d-sm-none v-divider theme--light" style="max-width: unset;">
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-images mx-n4 mx-sm-0 overflow-hidden v-sheet theme--light rounded-lg">
              <div data-v-1409cccc="" data-v-15d6fcda=""
                class="stay-availability-room-images stay-availability-room-images--grid" style="cursor: pointer;">
                <div data-v-1409cccc="" class="stay-availability-room-images__main-img grey lighten-4"
                  style="grid-area: main;">
                  <div data-v-1409cccc="" class="relative">
                    <div data-v-978962ea="" data-v-1409cccc=""
                      class="bg-transparent overflow-hidden v-sheet theme--light aspect-ratio"
                      style="height: 0px; max-width: 100%; width: 100%; padding-bottom: 66.6667%; line-height: 0;"><img
                        data-v-978962ea="" alt="Room"
                        src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/c6ddc7ec_b.jpg"
                        class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                    <div data-v-1409cccc=""
                      class="v-btn-stay-see-all-room-images absolute d-flex justify-center align-center rounded info elevation-1 ma-4 ma-sm-3 ma-md-4 px-2 py-1">
                      <span data-v-1409cccc="" aria-hidden="true"
                        class="v-icon notranslate mr-1 text--primary theme--light"
                        style="font-size: 16px; height: 16px; width: 16px;"><svg xmlns="http://www.w3.org/2000/svg"
                          viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                          style="font-size: 16px; height: 16px; width: 16px;">
                          <path
                            d="M10,4V8H14V4H10M16,4V8H20V4H16M16,10V14H20V10H16M16,16V20H20V16H16M14,20V16H10V20H14M8,20V16H4V20H8M8,14V10H4V14H8M8,8V4H4V8H8M10,14H14V10H10V14M4,2H20A2,2 0 0,1 22,4V20A2,2 0 0,1 20,22H4C2.92,22 2,21.1 2,20V4A2,2 0 0,1 4,2Z">
                          </path>
                        </svg></span> <span data-v-1409cccc="" class="pr-1 text-button text--primary font-weight-medium"
                        style="line-height: 1 !important;">
                        See Photos
                      </span></div>
                  </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-1;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/7f96225b_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-2;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/1b8343d0_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-3;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/73e0d399_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
              </div>
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-offer bg-transparent v-sheet v-sheet--outlined theme--light">
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--silverware-slashed v-icon--left theme--light"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1">Without breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          4,818,900
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 19,275,600
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--left theme--light success--text"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1 success--text">Free Breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          5,370,700
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 21,482,800
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div data-v-15d6fcda="">
            <div class="v-dialog__container"></div>
          </div>
        </div>
        <div data-v-d935b814="" class="gutters-0 d-sm-none v-sheet theme--light rounded-0 grey lighten-4"
          style="height: 24px;"></div> 
        <div data-v-15d6fcda="" data-v-d935b814="" elevation="0" class="bg-transparent mb-sm-8 mb-md-10">
          <div data-v-15d6fcda="" class="stay-offer-grid">
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-catalog gutters-0 gutters-sm-1 pa-4 v-sheet v-sheet--outlined theme--light"
              style="--sticky-top: 56px; --sticky-bg: #FFFFFF; max-width: unset !important;">
              <div data-v-15d6fcda="" class="d-flex justify-space-between align-sm-center">
                <div data-v-15d6fcda="" class="d-flex flex-nowrap align-start">
                  <div data-v-15d6fcda="" class="text-h5 font-weight-medium">
                    Fairmont Gold, Club Suite, 1 Double Bed
                  </div>
                </div> <button data-v-15d6fcda="" type="button"
                  class="my-sm-n1 mr-n1 ml-1 ml-sm-0 v-btn v-btn--rounded v-btn--text theme--light v-size--small primary--text"><span
                    class="v-btn__content"><span data-v-15d6fcda="" class="text-h8 font-weight-medium">
                      See details
                    </span></span></button>
              </div>
              <div data-v-15d6fcda="" class="d-inline-flex flex-wrap"><span data-v-15d6fcda="" class="pr-3"><span
                    data-v-15d6fcda="" aria-hidden="true" class="v-icon notranslate theme--light"
                    style="font-size: 18px; height: 18px; width: 18px;"><svg xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                      style="font-size: 18px; height: 18px; width: 18px;">
                      <path
                        d="M20 10V7A2 2 0 0 0 18 5H6A2 2 0 0 0 4 7V10A2 2 0 0 0 2 12V17H3.33L4 19H5L5.67 17H18.33L19 19H20L20.67 17H22V12A2 2 0 0 0 20 10M13 7H18V10H13M6 7H11V10H6M20 15H4V12H20Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">1 Double
                    Bed</span></span> <span data-v-15d6fcda="" class="pr-3"><span data-v-15d6fcda="" aria-hidden="true"
                    class="v-icon notranslate theme--light" style="font-size: 16px; height: 16px; width: 16px;"><svg
                      xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                      class="v-icon__svg" style="font-size: 16px; height: 16px; width: 16px;">
                      <path
                        d="M23,15H21V17H23V15M23,11H21V13H23V11M23,19H21V21C22,21 23,20 23,19M15,3H13V5H15V3M23,7H21V9H23V7M21,3V5H23C23,4 22,3 21,3M3,21H11V15H1V19A2,2 0 0,0 3,21M3,7H1V9H3V7M15,19H13V21H15V19M19,3H17V5H19V3M19,19H17V21H19V19M3,3C2,3 1,4 1,5H3V3M3,11H1V13H3V11M11,3H9V5H11V3M7,3H5V5H7V3Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">113 m<sup
                      data-v-15d6fcda="">2</sup></span></span> </div>
              <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                class="mx-n4 mt-4 mb-n4 d-sm-none v-divider theme--light" style="max-width: unset;">
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-images mx-n4 mx-sm-0 overflow-hidden v-sheet theme--light rounded-lg">
              <div data-v-1409cccc="" data-v-15d6fcda=""
                class="stay-availability-room-images stay-availability-room-images--grid" style="cursor: pointer;">
                <div data-v-1409cccc="" class="stay-availability-room-images__main-img grey lighten-4"
                  style="grid-area: main;">
                  <div data-v-1409cccc="" class="relative">
                    <div data-v-978962ea="" data-v-1409cccc=""
                      class="bg-transparent overflow-hidden v-sheet theme--light aspect-ratio"
                      style="height: 0px; max-width: 100%; width: 100%; padding-bottom: 66.6667%; line-height: 0;"><img
                        data-v-978962ea="" alt="Room"
                        src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/496d1f42_b.jpg"
                        class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                    <div data-v-1409cccc=""
                      class="v-btn-stay-see-all-room-images absolute d-flex justify-center align-center rounded info elevation-1 ma-4 ma-sm-3 ma-md-4 px-2 py-1">
                      <span data-v-1409cccc="" aria-hidden="true"
                        class="v-icon notranslate mr-1 text--primary theme--light"
                        style="font-size: 16px; height: 16px; width: 16px;"><svg xmlns="http://www.w3.org/2000/svg"
                          viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                          style="font-size: 16px; height: 16px; width: 16px;">
                          <path
                            d="M10,4V8H14V4H10M16,4V8H20V4H16M16,10V14H20V10H16M16,16V20H20V16H16M14,20V16H10V20H14M8,20V16H4V20H8M8,14V10H4V14H8M8,8V4H4V8H8M10,14H14V10H10V14M4,2H20A2,2 0 0,1 22,4V20A2,2 0 0,1 20,22H4C2.92,22 2,21.1 2,20V4A2,2 0 0,1 4,2Z">
                          </path>
                        </svg></span> <span data-v-1409cccc="" class="pr-1 text-button text--primary font-weight-medium"
                        style="line-height: 1 !important;">
                        See Photos
                      </span></div>
                  </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-1;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/7f96225b_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-2;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/73e0d399_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-3;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/096dfb7c_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
              </div>
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-offer bg-transparent v-sheet v-sheet--outlined theme--light">
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--silverware-slashed v-icon--left theme--light"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1">Without breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          5,148,700
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 20,594,800
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--left theme--light success--text"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1 success--text">Free Breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          5,700,400
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 22,801,600
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div data-v-15d6fcda="">
            <div class="v-dialog__container"></div>
          </div>
        </div>
        <div data-v-d935b814="" class="gutters-0 d-sm-none v-sheet theme--light rounded-0 grey lighten-4"
          style="height: 24px;"></div> 
        <div data-v-15d6fcda="" data-v-d935b814="" elevation="0" class="bg-transparent mb-sm-8 mb-md-10">
          <div data-v-15d6fcda="" class="stay-offer-grid">
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-catalog gutters-0 gutters-sm-1 pa-4 v-sheet v-sheet--outlined theme--light"
              style="--sticky-top: 56px; --sticky-bg: #FFFFFF; max-width: unset !important;">
              <div data-v-15d6fcda="" class="d-flex justify-space-between align-sm-center">
                <div data-v-15d6fcda="" class="d-flex flex-nowrap align-start">
                  <div data-v-15d6fcda="" class="text-h5 font-weight-medium">
                    Fairmont Gold, Suite, 1 King Bed with Sofa bed
                  </div>
                </div> <button data-v-15d6fcda="" type="button"
                  class="my-sm-n1 mr-n1 ml-1 ml-sm-0 v-btn v-btn--rounded v-btn--text theme--light v-size--small primary--text"><span
                    class="v-btn__content"><span data-v-15d6fcda="" class="text-h8 font-weight-medium">
                      See details
                    </span></span></button>
              </div>
              <div data-v-15d6fcda="" class="d-inline-flex flex-wrap"><span data-v-15d6fcda="" class="pr-3"><span
                    data-v-15d6fcda="" aria-hidden="true" class="v-icon notranslate theme--light"
                    style="font-size: 18px; height: 18px; width: 18px;"><svg xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                      style="font-size: 18px; height: 18px; width: 18px;">
                      <path
                        d="M20 10V7A2 2 0 0 0 18 5H6A2 2 0 0 0 4 7V10A2 2 0 0 0 2 12V17H3.33L4 19H5L5.67 17H18.33L19 19H20L20.67 17H22V12A2 2 0 0 0 20 10M13 7H18V10H13M6 7H11V10H6M20 15H4V12H20Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">1 King Bed and 1 Double
                    Sofa Bed</span></span> <span data-v-15d6fcda="" class="pr-3"><span data-v-15d6fcda=""
                    aria-hidden="true" class="v-icon notranslate theme--light"
                    style="font-size: 16px; height: 16px; width: 16px;"><svg xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                      style="font-size: 16px; height: 16px; width: 16px;">
                      <path
                        d="M23,15H21V17H23V15M23,11H21V13H23V11M23,19H21V21C22,21 23,20 23,19M15,3H13V5H15V3M23,7H21V9H23V7M21,3V5H23C23,4 22,3 21,3M3,21H11V15H1V19A2,2 0 0,0 3,21M3,7H1V9H3V7M15,19H13V21H15V19M19,3H17V5H19V3M19,19H17V21H19V19M3,3C2,3 1,4 1,5H3V3M3,11H1V13H3V11M11,3H9V5H11V3M7,3H5V5H7V3Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">113 m<sup
                      data-v-15d6fcda="">2</sup></span></span> </div>
              <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                class="mx-n4 mt-4 mb-n4 d-sm-none v-divider theme--light" style="max-width: unset;">
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-images mx-n4 mx-sm-0 overflow-hidden v-sheet theme--light rounded-lg">
              <div data-v-1409cccc="" data-v-15d6fcda=""
                class="stay-availability-room-images stay-availability-room-images--grid" style="cursor: pointer;">
                <div data-v-1409cccc="" class="stay-availability-room-images__main-img grey lighten-4"
                  style="grid-area: main;">
                  <div data-v-1409cccc="" class="relative">
                    <div data-v-978962ea="" data-v-1409cccc=""
                      class="bg-transparent overflow-hidden v-sheet theme--light aspect-ratio"
                      style="height: 0px; max-width: 100%; width: 100%; padding-bottom: 66.6667%; line-height: 0;"><img
                        data-v-978962ea="" alt="Room"
                        src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/496d1f42_b.jpg"
                        class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                    <div data-v-1409cccc=""
                      class="v-btn-stay-see-all-room-images absolute d-flex justify-center align-center rounded info elevation-1 ma-4 ma-sm-3 ma-md-4 px-2 py-1">
                      <span data-v-1409cccc="" aria-hidden="true"
                        class="v-icon notranslate mr-1 text--primary theme--light"
                        style="font-size: 16px; height: 16px; width: 16px;"><svg xmlns="http://www.w3.org/2000/svg"
                          viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                          style="font-size: 16px; height: 16px; width: 16px;">
                          <path
                            d="M10,4V8H14V4H10M16,4V8H20V4H16M16,10V14H20V10H16M16,16V20H20V16H16M14,20V16H10V20H14M8,20V16H4V20H8M8,14V10H4V14H8M8,8V4H4V8H8M10,14H14V10H10V14M4,2H20A2,2 0 0,1 22,4V20A2,2 0 0,1 20,22H4C2.92,22 2,21.1 2,20V4A2,2 0 0,1 4,2Z">
                          </path>
                        </svg></span> <span data-v-1409cccc="" class="pr-1 text-button text--primary font-weight-medium"
                        style="line-height: 1 !important;">
                        See Photos
                      </span></div>
                  </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-1;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/7f96225b_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-2;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/73e0d399_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-3;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/096dfb7c_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
              </div>
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-offer bg-transparent v-sheet v-sheet--outlined theme--light">
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--silverware-slashed v-icon--left theme--light"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1">Without breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          5,344,100
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 21,376,400
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--left theme--light success--text"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1 success--text">Free Breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          5,895,800
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 23,583,200
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div data-v-15d6fcda="">
            <div class="v-dialog__container"></div>
          </div>
        </div>
        <div data-v-d935b814="" class="gutters-0 d-sm-none v-sheet theme--light rounded-0 grey lighten-4"
          style="height: 24px;"></div> 
        <div data-v-15d6fcda="" data-v-d935b814="" elevation="0" class="bg-transparent mb-sm-8 mb-md-10">
          <div data-v-15d6fcda="" class="stay-offer-grid">
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-catalog gutters-0 gutters-sm-1 pa-4 v-sheet v-sheet--outlined theme--light"
              style="--sticky-top: 56px; --sticky-bg: #FFFFFF; max-width: unset !important;">
              <div data-v-15d6fcda="" class="d-flex justify-space-between align-sm-center">
                <div data-v-15d6fcda="" class="d-flex flex-nowrap align-start">
                  <div data-v-15d6fcda="" class="text-h5 font-weight-medium">
                    Suite, 1 Bedroom (Sky Suite)
                  </div>
                </div> <button data-v-15d6fcda="" type="button"
                  class="my-sm-n1 mr-n1 ml-1 ml-sm-0 v-btn v-btn--rounded v-btn--text theme--light v-size--small primary--text"><span
                    class="v-btn__content"><span data-v-15d6fcda="" class="text-h8 font-weight-medium">
                      See details
                    </span></span></button>
              </div>
              <div data-v-15d6fcda="" class="d-inline-flex flex-wrap"><span data-v-15d6fcda="" class="pr-3"><span
                    data-v-15d6fcda="" aria-hidden="true" class="v-icon notranslate theme--light"
                    style="font-size: 18px; height: 18px; width: 18px;"><svg xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                      style="font-size: 18px; height: 18px; width: 18px;">
                      <path
                        d="M20 10V7A2 2 0 0 0 18 5H6A2 2 0 0 0 4 7V10A2 2 0 0 0 2 12V17H3.33L4 19H5L5.67 17H18.33L19 19H20L20.67 17H22V12A2 2 0 0 0 20 10M13 7H18V10H13M6 7H11V10H6M20 15H4V12H20Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">1 Double
                    Bed</span></span> <span data-v-15d6fcda="" class="pr-3"><span data-v-15d6fcda="" aria-hidden="true"
                    class="v-icon notranslate theme--light" style="font-size: 16px; height: 16px; width: 16px;"><svg
                      xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                      class="v-icon__svg" style="font-size: 16px; height: 16px; width: 16px;">
                      <path
                        d="M23,15H21V17H23V15M23,11H21V13H23V11M23,19H21V21C22,21 23,20 23,19M15,3H13V5H15V3M23,7H21V9H23V7M21,3V5H23C23,4 22,3 21,3M3,21H11V15H1V19A2,2 0 0,0 3,21M3,7H1V9H3V7M15,19H13V21H15V19M19,3H17V5H19V3M19,19H17V21H19V19M3,3C2,3 1,4 1,5H3V3M3,11H1V13H3V11M11,3H9V5H11V3M7,3H5V5H7V3Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">85 m<sup
                      data-v-15d6fcda="">2</sup></span></span> </div>
              <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                class="mx-n4 mt-4 mb-n4 d-sm-none v-divider theme--light" style="max-width: unset;">
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-images mx-n4 mx-sm-0 overflow-hidden v-sheet theme--light rounded-lg">
              <div data-v-1409cccc="" data-v-15d6fcda=""
                class="stay-availability-room-images stay-availability-room-images--grid" style="cursor: pointer;">
                <div data-v-1409cccc="" class="stay-availability-room-images__main-img grey lighten-4"
                  style="grid-area: main;">
                  <div data-v-1409cccc="" class="relative">
                    <div data-v-978962ea="" data-v-1409cccc=""
                      class="bg-transparent overflow-hidden v-sheet theme--light aspect-ratio"
                      style="height: 0px; max-width: 100%; width: 100%; padding-bottom: 66.6667%; line-height: 0;"><img
                        data-v-978962ea="" alt="Room"
                        src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/6aaf50b4_b.jpg"
                        class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                    <div data-v-1409cccc=""
                      class="v-btn-stay-see-all-room-images absolute d-flex justify-center align-center rounded info elevation-1 ma-4 ma-sm-3 ma-md-4 px-2 py-1">
                      <span data-v-1409cccc="" aria-hidden="true"
                        class="v-icon notranslate mr-1 text--primary theme--light"
                        style="font-size: 16px; height: 16px; width: 16px;"><svg xmlns="http://www.w3.org/2000/svg"
                          viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                          style="font-size: 16px; height: 16px; width: 16px;">
                          <path
                            d="M10,4V8H14V4H10M16,4V8H20V4H16M16,10V14H20V10H16M16,16V20H20V16H16M14,20V16H10V20H14M8,20V16H4V20H8M8,14V10H4V14H8M8,8V4H4V8H8M10,14H14V10H10V14M4,2H20A2,2 0 0,1 22,4V20A2,2 0 0,1 20,22H4C2.92,22 2,21.1 2,20V4A2,2 0 0,1 4,2Z">
                          </path>
                        </svg></span> <span data-v-1409cccc="" class="pr-1 text-button text--primary font-weight-medium"
                        style="line-height: 1 !important;">
                        See Photos
                      </span></div>
                  </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-1;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/7f96225b_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-2;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/3e5dc054_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-3;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Bathroom"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/5db049b2_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
              </div>
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-offer bg-transparent v-sheet v-sheet--outlined theme--light">
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--silverware-slashed v-icon--left theme--light"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1">Without breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          5,352,600
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 21,410,400
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--left theme--light success--text"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1 success--text">Free Breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          5,904,400
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 23,617,600
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div data-v-15d6fcda="">
            <div class="v-dialog__container"></div>
          </div>
        </div>
        <div data-v-d935b814="" class="gutters-0 d-sm-none v-sheet theme--light rounded-0 grey lighten-4"
          style="height: 24px;"></div> 
        <div data-v-15d6fcda="" data-v-d935b814="" elevation="0" class="bg-transparent mb-sm-8 mb-md-10">
          <div data-v-15d6fcda="" class="stay-offer-grid">
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-catalog gutters-0 gutters-sm-1 pa-4 v-sheet v-sheet--outlined theme--light"
              style="--sticky-top: 56px; --sticky-bg: #FFFFFF; max-width: unset !important;">
              <div data-v-15d6fcda="" class="d-flex justify-space-between align-sm-center">
                <div data-v-15d6fcda="" class="d-flex flex-nowrap align-start">
                  <div data-v-15d6fcda="" class="text-h5 font-weight-medium">
                    Suite (Sky)
                  </div>
                </div> <button data-v-15d6fcda="" type="button"
                  class="my-sm-n1 mr-n1 ml-1 ml-sm-0 v-btn v-btn--rounded v-btn--text theme--light v-size--small primary--text"><span
                    class="v-btn__content"><span data-v-15d6fcda="" class="text-h8 font-weight-medium">
                      See details
                    </span></span></button>
              </div>
              <div data-v-15d6fcda="" class="d-inline-flex flex-wrap"><span data-v-15d6fcda="" class="pr-3"><span
                    data-v-15d6fcda="" aria-hidden="true" class="v-icon notranslate theme--light"
                    style="font-size: 18px; height: 18px; width: 18px;"><svg xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                      style="font-size: 18px; height: 18px; width: 18px;">
                      <path
                        d="M20 10V7A2 2 0 0 0 18 5H6A2 2 0 0 0 4 7V10A2 2 0 0 0 2 12V17H3.33L4 19H5L5.67 17H18.33L19 19H20L20.67 17H22V12A2 2 0 0 0 20 10M13 7H18V10H13M6 7H11V10H6M20 15H4V12H20Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">1 King Bed and 1 Double
                    Sofa Bed</span></span> <span data-v-15d6fcda="" class="pr-3"><span data-v-15d6fcda=""
                    aria-hidden="true" class="v-icon notranslate theme--light"
                    style="font-size: 16px; height: 16px; width: 16px;"><svg xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                      style="font-size: 16px; height: 16px; width: 16px;">
                      <path
                        d="M23,15H21V17H23V15M23,11H21V13H23V11M23,19H21V21C22,21 23,20 23,19M15,3H13V5H15V3M23,7H21V9H23V7M21,3V5H23C23,4 22,3 21,3M3,21H11V15H1V19A2,2 0 0,0 3,21M3,7H1V9H3V7M15,19H13V21H15V19M19,3H17V5H19V3M19,19H17V21H19V19M3,3C2,3 1,4 1,5H3V3M3,11H1V13H3V11M11,3H9V5H11V3M7,3H5V5H7V3Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">85 m<sup
                      data-v-15d6fcda="">2</sup></span></span> </div>
              <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                class="mx-n4 mt-4 mb-n4 d-sm-none v-divider theme--light" style="max-width: unset;">
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-images mx-n4 mx-sm-0 overflow-hidden v-sheet theme--light rounded-lg">
              <div data-v-1409cccc="" data-v-15d6fcda=""
                class="stay-availability-room-images stay-availability-room-images--grid" style="cursor: pointer;">
                <div data-v-1409cccc="" class="stay-availability-room-images__main-img grey lighten-4"
                  style="grid-area: main;">
                  <div data-v-1409cccc="" class="relative">
                    <div data-v-978962ea="" data-v-1409cccc=""
                      class="bg-transparent overflow-hidden v-sheet theme--light aspect-ratio"
                      style="height: 0px; max-width: 100%; width: 100%; padding-bottom: 66.6667%; line-height: 0;"><img
                        data-v-978962ea="" alt="Room"
                        src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/6aaf50b4_b.jpg"
                        class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                    <div data-v-1409cccc=""
                      class="v-btn-stay-see-all-room-images absolute d-flex justify-center align-center rounded info elevation-1 ma-4 ma-sm-3 ma-md-4 px-2 py-1">
                      <span data-v-1409cccc="" aria-hidden="true"
                        class="v-icon notranslate mr-1 text--primary theme--light"
                        style="font-size: 16px; height: 16px; width: 16px;"><svg xmlns="http://www.w3.org/2000/svg"
                          viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                          style="font-size: 16px; height: 16px; width: 16px;">
                          <path
                            d="M10,4V8H14V4H10M16,4V8H20V4H16M16,10V14H20V10H16M16,16V20H20V16H16M14,20V16H10V20H14M8,20V16H4V20H8M8,14V10H4V14H8M8,8V4H4V8H8M10,14H14V10H10V14M4,2H20A2,2 0 0,1 22,4V20A2,2 0 0,1 20,22H4C2.92,22 2,21.1 2,20V4A2,2 0 0,1 4,2Z">
                          </path>
                        </svg></span> <span data-v-1409cccc="" class="pr-1 text-button text--primary font-weight-medium"
                        style="line-height: 1 !important;">
                        See Photos
                      </span></div>
                  </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-1;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/7f96225b_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-2;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/a4305c49_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-3;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/3e5dc054_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
              </div>
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-offer bg-transparent v-sheet v-sheet--outlined theme--light">
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--silverware-slashed v-icon--left theme--light"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1">Without breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          5,536,600
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 22,146,400
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--left theme--light success--text"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1 success--text">Free Breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          6,088,300
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 24,353,200
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div data-v-15d6fcda="">
            <div class="v-dialog__container"></div>
          </div>
        </div>
        <div data-v-d935b814="" class="gutters-0 d-sm-none v-sheet theme--light rounded-0 grey lighten-4"
          style="height: 24px;"></div> 
        <div data-v-15d6fcda="" data-v-d935b814="" elevation="0" class="bg-transparent mb-sm-8 mb-md-10">
          <div data-v-15d6fcda="" class="stay-offer-grid">
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-catalog gutters-0 gutters-sm-1 pa-4 v-sheet v-sheet--outlined theme--light"
              style="--sticky-top: 56px; --sticky-bg: #FFFFFF; max-width: unset !important;">
              <div data-v-15d6fcda="" class="d-flex justify-space-between align-sm-center">
                <div data-v-15d6fcda="" class="d-flex flex-nowrap align-start">
                  <div data-v-15d6fcda="" class="text-h5 font-weight-medium">
                    Suite, 2 Bedrooms (Sky Suite)
                  </div>
                </div> <button data-v-15d6fcda="" type="button"
                  class="my-sm-n1 mr-n1 ml-1 ml-sm-0 v-btn v-btn--rounded v-btn--text theme--light v-size--small primary--text"><span
                    class="v-btn__content"><span data-v-15d6fcda="" class="text-h8 font-weight-medium">
                      See details
                    </span></span></button>
              </div>
              <div data-v-15d6fcda="" class="d-inline-flex flex-wrap"><span data-v-15d6fcda="" class="pr-3"><span
                    data-v-15d6fcda="" aria-hidden="true" class="v-icon notranslate theme--light"
                    style="font-size: 18px; height: 18px; width: 18px;"><svg xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                      style="font-size: 18px; height: 18px; width: 18px;">
                      <path
                        d="M20 10V7A2 2 0 0 0 18 5H6A2 2 0 0 0 4 7V10A2 2 0 0 0 2 12V17H3.33L4 19H5L5.67 17H18.33L19 19H20L20.67 17H22V12A2 2 0 0 0 20 10M13 7H18V10H13M6 7H11V10H6M20 15H4V12H20Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">1 Double
                    Bed</span></span> <span data-v-15d6fcda="" class="pr-3"><span data-v-15d6fcda="" aria-hidden="true"
                    class="v-icon notranslate theme--light" style="font-size: 16px; height: 16px; width: 16px;"><svg
                      xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                      class="v-icon__svg" style="font-size: 16px; height: 16px; width: 16px;">
                      <path
                        d="M23,15H21V17H23V15M23,11H21V13H23V11M23,19H21V21C22,21 23,20 23,19M15,3H13V5H15V3M23,7H21V9H23V7M21,3V5H23C23,4 22,3 21,3M3,21H11V15H1V19A2,2 0 0,0 3,21M3,7H1V9H3V7M15,19H13V21H15V19M19,3H17V5H19V3M19,19H17V21H19V19M3,3C2,3 1,4 1,5H3V3M3,11H1V13H3V11M11,3H9V5H11V3M7,3H5V5H7V3Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">113 m<sup
                      data-v-15d6fcda="">2</sup></span></span> </div>
              <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                class="mx-n4 mt-4 mb-n4 d-sm-none v-divider theme--light" style="max-width: unset;">
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-images mx-n4 mx-sm-0 overflow-hidden v-sheet theme--light rounded-lg">
              <div data-v-1409cccc="" data-v-15d6fcda=""
                class="stay-availability-room-images stay-availability-room-images--grid" style="cursor: pointer;">
                <div data-v-1409cccc="" class="stay-availability-room-images__main-img grey lighten-4"
                  style="grid-area: main;">
                  <div data-v-1409cccc="" class="relative">
                    <div data-v-978962ea="" data-v-1409cccc=""
                      class="bg-transparent overflow-hidden v-sheet theme--light aspect-ratio"
                      style="height: 0px; max-width: 100%; width: 100%; padding-bottom: 66.6667%; line-height: 0;"><img
                        data-v-978962ea="" alt="Room"
                        src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/e49faafe_b.jpg"
                        class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                    <div data-v-1409cccc=""
                      class="v-btn-stay-see-all-room-images absolute d-flex justify-center align-center rounded info elevation-1 ma-4 ma-sm-3 ma-md-4 px-2 py-1">
                      <span data-v-1409cccc="" aria-hidden="true"
                        class="v-icon notranslate mr-1 text--primary theme--light"
                        style="font-size: 16px; height: 16px; width: 16px;"><svg xmlns="http://www.w3.org/2000/svg"
                          viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                          style="font-size: 16px; height: 16px; width: 16px;">
                          <path
                            d="M10,4V8H14V4H10M16,4V8H20V4H16M16,10V14H20V10H16M16,16V20H20V16H16M14,20V16H10V20H14M8,20V16H4V20H8M8,14V10H4V14H8M8,8V4H4V8H8M10,14H14V10H10V14M4,2H20A2,2 0 0,1 22,4V20A2,2 0 0,1 20,22H4C2.92,22 2,21.1 2,20V4A2,2 0 0,1 4,2Z">
                          </path>
                        </svg></span> <span data-v-1409cccc="" class="pr-1 text-button text--primary font-weight-medium"
                        style="line-height: 1 !important;">
                        See Photos
                      </span></div>
                  </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-1;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/7f96225b_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-2;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/46804fa1_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-3;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/6aaf50b4_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
              </div>
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-offer bg-transparent v-sheet v-sheet--outlined theme--light">
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--silverware-slashed v-icon--left theme--light"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1">Without breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          7,053,900
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 28,215,600
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--left theme--light success--text"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1 success--text">Free Breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          7,605,700
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 30,422,800
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div data-v-15d6fcda="">
            <div class="v-dialog__container"></div>
          </div>
        </div>
        <div data-v-d935b814="" class="gutters-0 d-sm-none v-sheet theme--light rounded-0 grey lighten-4"
          style="height: 24px;"></div> 
        <div data-v-15d6fcda="" data-v-d935b814="" elevation="0" class="bg-transparent mb-sm-8 mb-md-10">
          <div data-v-15d6fcda="" class="stay-offer-grid">
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-catalog gutters-0 gutters-sm-1 pa-4 v-sheet v-sheet--outlined theme--light"
              style="--sticky-top: 56px; --sticky-bg: #FFFFFF; max-width: unset !important;">
              <div data-v-15d6fcda="" class="d-flex justify-space-between align-sm-center">
                <div data-v-15d6fcda="" class="d-flex flex-nowrap align-start">
                  <div data-v-15d6fcda="" class="text-h5 font-weight-medium">
                    Suite, 2 Bedrooms, Smoking (Sky Suite)
                  </div>
                </div> <button data-v-15d6fcda="" type="button"
                  class="my-sm-n1 mr-n1 ml-1 ml-sm-0 v-btn v-btn--rounded v-btn--text theme--light v-size--small primary--text"><span
                    class="v-btn__content"><span data-v-15d6fcda="" class="text-h8 font-weight-medium">
                      See details
                    </span></span></button>
              </div>
              <div data-v-15d6fcda="" class="d-inline-flex flex-wrap"><span data-v-15d6fcda="" class="pr-3"><span
                    data-v-15d6fcda="" aria-hidden="true" class="v-icon notranslate theme--light"
                    style="font-size: 18px; height: 18px; width: 18px;"><svg xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                      style="font-size: 18px; height: 18px; width: 18px;">
                      <path
                        d="M20 10V7A2 2 0 0 0 18 5H6A2 2 0 0 0 4 7V10A2 2 0 0 0 2 12V17H3.33L4 19H5L5.67 17H18.33L19 19H20L20.67 17H22V12A2 2 0 0 0 20 10M13 7H18V10H13M6 7H11V10H6M20 15H4V12H20Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">1 King Bed and 2 Double
                    Beds</span></span> <span data-v-15d6fcda="" class="pr-3"><span data-v-15d6fcda="" aria-hidden="true"
                    class="v-icon notranslate theme--light" style="font-size: 16px; height: 16px; width: 16px;"><svg
                      xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                      class="v-icon__svg" style="font-size: 16px; height: 16px; width: 16px;">
                      <path
                        d="M23,15H21V17H23V15M23,11H21V13H23V11M23,19H21V21C22,21 23,20 23,19M15,3H13V5H15V3M23,7H21V9H23V7M21,3V5H23C23,4 22,3 21,3M3,21H11V15H1V19A2,2 0 0,0 3,21M3,7H1V9H3V7M15,19H13V21H15V19M19,3H17V5H19V3M19,19H17V21H19V19M3,3C2,3 1,4 1,5H3V3M3,11H1V13H3V11M11,3H9V5H11V3M7,3H5V5H7V3Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">128 m<sup
                      data-v-15d6fcda="">2</sup></span></span> </div>
              <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                class="mx-n4 mt-4 mb-n4 d-sm-none v-divider theme--light" style="max-width: unset;">
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-images mx-n4 mx-sm-0 overflow-hidden v-sheet theme--light rounded-lg">
              <div data-v-1409cccc="" data-v-15d6fcda=""
                class="stay-availability-room-images stay-availability-room-images--grid" style="cursor: pointer;">
                <div data-v-1409cccc="" class="stay-availability-room-images__main-img grey lighten-4"
                  style="grid-area: main;">
                  <div data-v-1409cccc="" class="relative">
                    <div data-v-978962ea="" data-v-1409cccc=""
                      class="bg-transparent overflow-hidden v-sheet theme--light aspect-ratio"
                      style="height: 0px; max-width: 100%; width: 100%; padding-bottom: 66.6667%; line-height: 0;"><img
                        data-v-978962ea="" alt="Room"
                        src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/e49faafe_b.jpg"
                        class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                    <div data-v-1409cccc=""
                      class="v-btn-stay-see-all-room-images absolute d-flex justify-center align-center rounded info elevation-1 ma-4 ma-sm-3 ma-md-4 px-2 py-1">
                      <span data-v-1409cccc="" aria-hidden="true"
                        class="v-icon notranslate mr-1 text--primary theme--light"
                        style="font-size: 16px; height: 16px; width: 16px;"><svg xmlns="http://www.w3.org/2000/svg"
                          viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                          style="font-size: 16px; height: 16px; width: 16px;">
                          <path
                            d="M10,4V8H14V4H10M16,4V8H20V4H16M16,10V14H20V10H16M16,16V20H20V16H16M14,20V16H10V20H14M8,20V16H4V20H8M8,14V10H4V14H8M8,8V4H4V8H8M10,14H14V10H10V14M4,2H20A2,2 0 0,1 22,4V20A2,2 0 0,1 20,22H4C2.92,22 2,21.1 2,20V4A2,2 0 0,1 4,2Z">
                          </path>
                        </svg></span> <span data-v-1409cccc="" class="pr-1 text-button text--primary font-weight-medium"
                        style="line-height: 1 !important;">
                        See Photos
                      </span></div>
                  </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-1;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/7f96225b_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-2;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/46804fa1_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-3;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/6aaf50b4_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
              </div>
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-offer bg-transparent v-sheet v-sheet--outlined theme--light">
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--silverware-slashed v-icon--left theme--light"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1">Without breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          7,237,800
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 28,951,200
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--left theme--light success--text"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1 success--text">Free Breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          7,789,600
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 31,158,400
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div data-v-15d6fcda="">
            <div class="v-dialog__container"></div>
          </div>
        </div>
        <div data-v-d935b814="" class="gutters-0 d-sm-none v-sheet theme--light rounded-0 grey lighten-4"
          style="height: 24px;"></div> 
        <div data-v-15d6fcda="" data-v-d935b814="" elevation="0" class="bg-transparent mb-sm-8 mb-md-10">
          <div data-v-15d6fcda="" class="stay-offer-grid">
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-catalog gutters-0 gutters-sm-1 pa-4 v-sheet v-sheet--outlined theme--light"
              style="--sticky-top: 56px; --sticky-bg: #FFFFFF; max-width: unset !important;">
              <div data-v-15d6fcda="" class="d-flex justify-space-between align-sm-center">
                <div data-v-15d6fcda="" class="d-flex flex-nowrap align-start">
                  <div data-v-15d6fcda="" class="text-h5 font-weight-medium">
                    Fairmont Gold, Club Room, 2 Queen Beds
                  </div>
                </div> <button data-v-15d6fcda="" type="button"
                  class="my-sm-n1 mr-n1 ml-1 ml-sm-0 v-btn v-btn--rounded v-btn--text theme--light v-size--small primary--text"><span
                    class="v-btn__content"><span data-v-15d6fcda="" class="text-h8 font-weight-medium">
                      See details
                    </span></span></button>
              </div>
              <div data-v-15d6fcda="" class="d-inline-flex flex-wrap"><span data-v-15d6fcda="" class="pr-3"><span
                    data-v-15d6fcda="" aria-hidden="true" class="v-icon notranslate theme--light"
                    style="font-size: 18px; height: 18px; width: 18px;"><svg xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                      style="font-size: 18px; height: 18px; width: 18px;">
                      <path
                        d="M20 10V7A2 2 0 0 0 18 5H6A2 2 0 0 0 4 7V10A2 2 0 0 0 2 12V17H3.33L4 19H5L5.67 17H18.33L19 19H20L20.67 17H22V12A2 2 0 0 0 20 10M13 7H18V10H13M6 7H11V10H6M20 15H4V12H20Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">2 Queen
                    Beds</span></span> <span data-v-15d6fcda="" class="pr-3"><span data-v-15d6fcda="" aria-hidden="true"
                    class="v-icon notranslate theme--light" style="font-size: 16px; height: 16px; width: 16px;"><svg
                      xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                      class="v-icon__svg" style="font-size: 16px; height: 16px; width: 16px;">
                      <path
                        d="M23,15H21V17H23V15M23,11H21V13H23V11M23,19H21V21C22,21 23,20 23,19M15,3H13V5H15V3M23,7H21V9H23V7M21,3V5H23C23,4 22,3 21,3M3,21H11V15H1V19A2,2 0 0,0 3,21M3,7H1V9H3V7M15,19H13V21H15V19M19,3H17V5H19V3M19,19H17V21H19V19M3,3C2,3 1,4 1,5H3V3M3,11H1V13H3V11M11,3H9V5H11V3M7,3H5V5H7V3Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">49 m<sup
                      data-v-15d6fcda="">2</sup></span></span> </div>
              <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                class="mx-n4 mt-4 mb-n4 d-sm-none v-divider theme--light" style="max-width: unset;">
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-images mx-n4 mx-sm-0 overflow-hidden v-sheet theme--light rounded-lg">
              <div data-v-1409cccc="" data-v-15d6fcda=""
                class="stay-availability-room-images stay-availability-room-images--grid" style="cursor: pointer;">
                <div data-v-1409cccc="" class="stay-availability-room-images__main-img grey lighten-4"
                  style="grid-area: main;">
                  <div data-v-1409cccc="" class="relative">
                    <div data-v-978962ea="" data-v-1409cccc=""
                      class="bg-transparent overflow-hidden v-sheet theme--light aspect-ratio"
                      style="height: 0px; max-width: 100%; width: 100%; padding-bottom: 66.6667%; line-height: 0;"><img
                        data-v-978962ea="" alt="Room"
                        src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/5408c18a_b.jpg"
                        class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                    <div data-v-1409cccc=""
                      class="v-btn-stay-see-all-room-images absolute d-flex justify-center align-center rounded info elevation-1 ma-4 ma-sm-3 ma-md-4 px-2 py-1">
                      <span data-v-1409cccc="" aria-hidden="true"
                        class="v-icon notranslate mr-1 text--primary theme--light"
                        style="font-size: 16px; height: 16px; width: 16px;"><svg xmlns="http://www.w3.org/2000/svg"
                          viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                          style="font-size: 16px; height: 16px; width: 16px;">
                          <path
                            d="M10,4V8H14V4H10M16,4V8H20V4H16M16,10V14H20V10H16M16,16V20H20V16H16M14,20V16H10V20H14M8,20V16H4V20H8M8,14V10H4V14H8M8,8V4H4V8H8M10,14H14V10H10V14M4,2H20A2,2 0 0,1 22,4V20A2,2 0 0,1 20,22H4C2.92,22 2,21.1 2,20V4A2,2 0 0,1 4,2Z">
                          </path>
                        </svg></span> <span data-v-1409cccc="" class="pr-1 text-button text--primary font-weight-medium"
                        style="line-height: 1 !important;">
                        See Photos
                      </span></div>
                  </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-1;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/7f96225b_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-2;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/096dfb7c_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-3;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/696f146a_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
              </div>
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-offer bg-transparent v-sheet v-sheet--outlined theme--light">
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--silverware-slashed v-icon--left theme--light"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1">Without breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          8,629,500
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 34,518,000
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--left theme--light success--text"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1 success--text">Free Breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          9,181,200
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 36,724,800
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div data-v-15d6fcda="">
            <div class="v-dialog__container"></div>
          </div>
        </div>
        <div data-v-d935b814="" class="gutters-0 d-sm-none v-sheet theme--light rounded-0 grey lighten-4"
          style="height: 24px;"></div> 
        <div data-v-15d6fcda="" data-v-d935b814="" elevation="0" class="bg-transparent mb-sm-8 mb-md-10">
          <div data-v-15d6fcda="" class="stay-offer-grid">
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-catalog gutters-0 gutters-sm-1 pa-4 v-sheet v-sheet--outlined theme--light"
              style="--sticky-top: 56px; --sticky-bg: #FFFFFF; max-width: unset !important;">
              <div data-v-15d6fcda="" class="d-flex justify-space-between align-sm-center">
                <div data-v-15d6fcda="" class="d-flex flex-nowrap align-start">
                  <div data-v-15d6fcda="" class="text-h5 font-weight-medium">
                    Fairmont, Signature Suite, 1 Bedroom
                  </div>
                </div> <button data-v-15d6fcda="" type="button"
                  class="my-sm-n1 mr-n1 ml-1 ml-sm-0 v-btn v-btn--rounded v-btn--text theme--light v-size--small primary--text"><span
                    class="v-btn__content"><span data-v-15d6fcda="" class="text-h8 font-weight-medium">
                      See details
                    </span></span></button>
              </div>
              <div data-v-15d6fcda="" class="d-inline-flex flex-wrap"><span data-v-15d6fcda="" class="pr-3"><span
                    data-v-15d6fcda="" aria-hidden="true" class="v-icon notranslate theme--light"
                    style="font-size: 18px; height: 18px; width: 18px;"><svg xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                      style="font-size: 18px; height: 18px; width: 18px;">
                      <path
                        d="M20 10V7A2 2 0 0 0 18 5H6A2 2 0 0 0 4 7V10A2 2 0 0 0 2 12V17H3.33L4 19H5L5.67 17H18.33L19 19H20L20.67 17H22V12A2 2 0 0 0 20 10M13 7H18V10H13M6 7H11V10H6M20 15H4V12H20Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">1 Double
                    Bed</span></span> <span data-v-15d6fcda="" class="pr-3"><span data-v-15d6fcda="" aria-hidden="true"
                    class="v-icon notranslate theme--light" style="font-size: 16px; height: 16px; width: 16px;"><svg
                      xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                      class="v-icon__svg" style="font-size: 16px; height: 16px; width: 16px;">
                      <path
                        d="M23,15H21V17H23V15M23,11H21V13H23V11M23,19H21V21C22,21 23,20 23,19M15,3H13V5H15V3M23,7H21V9H23V7M21,3V5H23C23,4 22,3 21,3M3,21H11V15H1V19A2,2 0 0,0 3,21M3,7H1V9H3V7M15,19H13V21H15V19M19,3H17V5H19V3M19,19H17V21H19V19M3,3C2,3 1,4 1,5H3V3M3,11H1V13H3V11M11,3H9V5H11V3M7,3H5V5H7V3Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">129 m<sup
                      data-v-15d6fcda="">2</sup></span></span> </div>
              <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                class="mx-n4 mt-4 mb-n4 d-sm-none v-divider theme--light" style="max-width: unset;">
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-images mx-n4 mx-sm-0 overflow-hidden v-sheet theme--light rounded-lg">
              <div data-v-1409cccc="" data-v-15d6fcda=""
                class="stay-availability-room-images stay-availability-room-images--grid" style="cursor: pointer;">
                <div data-v-1409cccc="" class="stay-availability-room-images__main-img grey lighten-4"
                  style="grid-area: main;">
                  <div data-v-1409cccc="" class="relative">
                    <div data-v-978962ea="" data-v-1409cccc=""
                      class="bg-transparent overflow-hidden v-sheet theme--light aspect-ratio"
                      style="height: 0px; max-width: 100%; width: 100%; padding-bottom: 66.6667%; line-height: 0;"><img
                        data-v-978962ea="" alt="Room"
                        src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/w3369h2248x0y0-a8305800_b.jpg"
                        class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                    <div data-v-1409cccc=""
                      class="v-btn-stay-see-all-room-images absolute d-flex justify-center align-center rounded info elevation-1 ma-4 ma-sm-3 ma-md-4 px-2 py-1">
                      <span data-v-1409cccc="" aria-hidden="true"
                        class="v-icon notranslate mr-1 text--primary theme--light"
                        style="font-size: 16px; height: 16px; width: 16px;"><svg xmlns="http://www.w3.org/2000/svg"
                          viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                          style="font-size: 16px; height: 16px; width: 16px;">
                          <path
                            d="M10,4V8H14V4H10M16,4V8H20V4H16M16,10V14H20V10H16M16,16V20H20V16H16M14,20V16H10V20H14M8,20V16H4V20H8M8,14V10H4V14H8M8,8V4H4V8H8M10,14H14V10H10V14M4,2H20A2,2 0 0,1 22,4V20A2,2 0 0,1 20,22H4C2.92,22 2,21.1 2,20V4A2,2 0 0,1 4,2Z">
                          </path>
                        </svg></span> <span data-v-1409cccc="" class="pr-1 text-button text--primary font-weight-medium"
                        style="line-height: 1 !important;">
                        See Photos
                      </span></div>
                  </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-1;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/7f96225b_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-2;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/002087e1_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-3;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/5139b1b5_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
              </div>
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-offer bg-transparent v-sheet v-sheet--outlined theme--light">
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--silverware-slashed v-icon--left theme--light"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1">Without breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          10,363,800
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 41,455,200
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--left theme--light success--text"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1 success--text">Free Breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          10,915,500
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 43,662,000
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div data-v-15d6fcda="">
            <div class="v-dialog__container"></div>
          </div>
        </div>
        <div data-v-d935b814="" class="gutters-0 d-sm-none v-sheet theme--light rounded-0 grey lighten-4"
          style="height: 24px;"></div> 
        <div data-v-15d6fcda="" data-v-d935b814="" elevation="0" class="bg-transparent mb-sm-8 mb-md-10">
          <div data-v-15d6fcda="" class="stay-offer-grid">
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-catalog gutters-0 gutters-sm-1 pa-4 v-sheet v-sheet--outlined theme--light"
              style="--sticky-top: 56px; --sticky-bg: #FFFFFF; max-width: unset !important;">
              <div data-v-15d6fcda="" class="d-flex justify-space-between align-sm-center">
                <div data-v-15d6fcda="" class="d-flex flex-nowrap align-start">
                  <div data-v-15d6fcda="" class="text-h5 font-weight-medium">
                    Fairmont, Signature Suite, 2 Bedrooms
                  </div>
                </div> <button data-v-15d6fcda="" type="button"
                  class="my-sm-n1 mr-n1 ml-1 ml-sm-0 v-btn v-btn--rounded v-btn--text theme--light v-size--small primary--text"><span
                    class="v-btn__content"><span data-v-15d6fcda="" class="text-h8 font-weight-medium">
                      See details
                    </span></span></button>
              </div>
              <div data-v-15d6fcda="" class="d-inline-flex flex-wrap"><span data-v-15d6fcda="" class="pr-3"><span
                    data-v-15d6fcda="" aria-hidden="true" class="v-icon notranslate theme--light"
                    style="font-size: 18px; height: 18px; width: 18px;"><svg xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                      style="font-size: 18px; height: 18px; width: 18px;">
                      <path
                        d="M20 10V7A2 2 0 0 0 18 5H6A2 2 0 0 0 4 7V10A2 2 0 0 0 2 12V17H3.33L4 19H5L5.67 17H18.33L19 19H20L20.67 17H22V12A2 2 0 0 0 20 10M13 7H18V10H13M6 7H11V10H6M20 15H4V12H20Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">1 King Bed and 2 Twin
                    Beds</span></span> <span data-v-15d6fcda="" class="pr-3"><span data-v-15d6fcda="" aria-hidden="true"
                    class="v-icon notranslate theme--light" style="font-size: 16px; height: 16px; width: 16px;"><svg
                      xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                      class="v-icon__svg" style="font-size: 16px; height: 16px; width: 16px;">
                      <path
                        d="M23,15H21V17H23V15M23,11H21V13H23V11M23,19H21V21C22,21 23,20 23,19M15,3H13V5H15V3M23,7H21V9H23V7M21,3V5H23C23,4 22,3 21,3M3,21H11V15H1V19A2,2 0 0,0 3,21M3,7H1V9H3V7M15,19H13V21H15V19M19,3H17V5H19V3M19,19H17V21H19V19M3,3C2,3 1,4 1,5H3V3M3,11H1V13H3V11M11,3H9V5H11V3M7,3H5V5H7V3Z">
                      </path>
                    </svg></span> <span data-v-15d6fcda="" class="text-caption text-md-body-2">172 m<sup
                      data-v-15d6fcda="">2</sup></span></span> </div>
              <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                class="mx-n4 mt-4 mb-n4 d-sm-none v-divider theme--light" style="max-width: unset;">
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-images mx-n4 mx-sm-0 overflow-hidden v-sheet theme--light rounded-lg">
              <div data-v-1409cccc="" data-v-15d6fcda=""
                class="stay-availability-room-images stay-availability-room-images--grid" style="cursor: pointer;">
                <div data-v-1409cccc="" class="stay-availability-room-images__main-img grey lighten-4"
                  style="grid-area: main;">
                  <div data-v-1409cccc="" class="relative">
                    <div data-v-978962ea="" data-v-1409cccc=""
                      class="bg-transparent overflow-hidden v-sheet theme--light aspect-ratio"
                      style="height: 0px; max-width: 100%; width: 100%; padding-bottom: 66.6667%; line-height: 0;"><img
                        data-v-978962ea="" alt="Room"
                        src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/4e3881ed_b.jpg"
                        class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                    <div data-v-1409cccc=""
                      class="v-btn-stay-see-all-room-images absolute d-flex justify-center align-center rounded info elevation-1 ma-4 ma-sm-3 ma-md-4 px-2 py-1">
                      <span data-v-1409cccc="" aria-hidden="true"
                        class="v-icon notranslate mr-1 text--primary theme--light"
                        style="font-size: 16px; height: 16px; width: 16px;"><svg xmlns="http://www.w3.org/2000/svg"
                          viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                          style="font-size: 16px; height: 16px; width: 16px;">
                          <path
                            d="M10,4V8H14V4H10M16,4V8H20V4H16M16,10V14H20V10H16M16,16V20H20V16H16M14,20V16H10V20H14M8,20V16H4V20H8M8,14V10H4V14H8M8,8V4H4V8H8M10,14H14V10H10V14M4,2H20A2,2 0 0,1 22,4V20A2,2 0 0,1 20,22H4C2.92,22 2,21.1 2,20V4A2,2 0 0,1 4,2Z">
                          </path>
                        </svg></span> <span data-v-1409cccc="" class="pr-1 text-button text--primary font-weight-medium"
                        style="line-height: 1 !important;">
                        See Photos
                      </span></div>
                  </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-1;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/7f96225b_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-2;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/002087e1_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
                <div data-v-1409cccc="" class="grey lighten-4 relative stay-availability-room-images__other-img"
                  style="line-height: 0; grid-area: other-3;">
                  <div data-v-978962ea="" data-v-1409cccc=""
                    class="bg-transparent overflow-hidden stay-availability-room-images__other-img__container v-sheet theme--light aspect-ratio"
                    style="height: 0px; width: 100%; padding-bottom: 100%;"><img data-v-978962ea="" alt="Room"
                      src="https://i.travelapi.com/lodging/10000000/9300000/9296600/9296574/fc2eea0f_b.jpg"
                      class="w-full h-full" style="object-fit: cover; object-position: 50% 50%;"> </div>
                </div>
              </div>
            </div>
            <div data-v-15d6fcda=""
              class="stay-offer-grid__room-offer bg-transparent v-sheet v-sheet--outlined theme--light">
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--silverware-slashed v-icon--left theme--light"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1">Without breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          13,295,000
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 53,180,000
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
              <div data-v-15d6fcda="" class="py-4 pa-sm-4 bg-transparent v-sheet theme--light">
                <hr data-v-15d6fcda="" role="separator" aria-orientation="horizontal"
                  class="mx-n4 mt-n4 mb-4 v-divider theme--light" style="max-width: unset; opacity: 0.69;">
                <div data-v-15d6fcda="" class="row flex-nowrap align-stretch justify-space-between">
                  <div data-v-15d6fcda="" class="col col-auto" style="flex: 1 0 0%; min-width: 0px;">
                    <div data-v-15d6fcda="">
                      <div data-v-15d6fcda="" id="meal-plan" class="d-flex align-baseline"><span
                          data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                            class="v-icon notranslate v-icon--left theme--light success--text"
                            style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                              viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                              style="font-size: 17px; height: 17px; width: 17px;">
                              <path
                                d="M11,9H9V2H7V9H5V2H3V9C3,11.12 4.66,12.84 6.75,12.97V22H9.25V12.97C11.34,12.84 13,11.12 13,9V2H11V9M16,6V14H18.5V22H21V2C18.24,2 16,4.24 16,6Z">
                              </path>
                            </svg></span></span> <span data-v-15d6fcda=""
                          class="align-middle text-body-2 text-md-body-1 success--text">Free Breakfast</span></div>
                    </div>
                    <div data-v-15d6fcda="" id="cancel-policy" class="d-flex align-baseline"><span
                        data-v-15d6fcda=""><span data-v-15d6fcda="" aria-hidden="true"
                          class="v-icon notranslate v-icon--left theme--light success--text"
                          style="font-size: 17px; height: 17px; width: 17px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 17px; height: 17px; width: 17px;">
                            <path
                              d="M13 19C13 18.66 13.04 18.33 13.09 18H3V12H19V13C19.7 13 20.37 13.13 21 13.35V6C21 4.89 20.11 4 19 4H3C1.89 4 1 4.89 1 6V18C1 19.1 1.89 20 3 20H13.09C13.04 19.67 13 19.34 13 19M3 6H19V8H3V6M17.75 22L15 19L16.16 17.84L17.75 19.43L21.34 15.84L22.5 17.25L17.75 22">
                            </path>
                          </svg></span></span> <span data-v-15d6fcda=""
                        class="align-middle text-body-2 text-md-body-1 success--text">Free cancellation before 01 Mar
                        2025</span></div>
                  </div>
                  <div data-v-15d6fcda="" class="d-flex justify-end col col-auto"
                    style="flex: 0 0 auto; min-width: 144px;">
                    <div data-v-4ff6fa5e="" data-v-15d6fcda="" class="d-inline-block my-n1">
                      <div data-v-4ff6fa5e="" class="d-flex flex-row flex-nowrap align-center" style="gap: 4px;"><button
                          data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 20px; height: 20px; width: 20px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 20px; height: 20px; width: 20px;">
                                <path
                                  d="M19,21H8V7H19M19,5H8A2,2 0 0,0 6,7V21A2,2 0 0,0 8,23H19A2,2 0 0,0 21,21V7A2,2 0 0,0 19,5M16,1H4A2,2 0 0,0 2,3V17H4V3H16V1Z">
                                </path>
                              </svg></span></span></button><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span> <span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;"><span class="v-btn__content"><span data-v-4ff6fa5e=""
                              aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M19 19H15V21H19C20.1 21 21 20.1 21 19V15H19M19 3H15V5H19V9H21V5C21 3.9 20.1 3 19 3M5 5H9V3H5C3.9 3 3 3.9 3 5V9H5M5 15H3V19C3 20.1 3.9 21 5 21H9V19H5V15M7 11H9V13H7V11M11 11H13V13H11V11M15 11H17V13H15V11Z">
                                </path>
                              </svg></span></span></button>
                        <div data-v-4ff6fa5e="" class="v-dialog__container"></div><span data-v-4ff6fa5e=""
                          class="v-tooltip v-tooltip--top"></span><button data-v-4ff6fa5e="" type="button"
                          class="v-btn v-btn--icon v-btn--round theme--light v-size--x-small"
                          style="height: 32px; width: 32px;" id="stay-availability-menu-button" role="button"
                          aria-haspopup="true" aria-expanded="false"><span class="v-btn__content"><span
                              data-v-4ff6fa5e="" aria-hidden="true" class="v-icon notranslate theme--light"
                              style="font-size: 22px; height: 22px; width: 22px;"><svg
                                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" role="img" aria-hidden="true"
                                class="v-icon__svg" style="font-size: 22px; height: 22px; width: 22px;">
                                <path
                                  d="M16,12A2,2 0 0,1 18,10A2,2 0 0,1 20,12A2,2 0 0,1 18,14A2,2 0 0,1 16,12M10,12A2,2 0 0,1 12,10A2,2 0 0,1 14,12A2,2 0 0,1 12,14A2,2 0 0,1 10,12M4,12A2,2 0 0,1 6,10A2,2 0 0,1 8,12A2,2 0 0,1 6,14A2,2 0 0,1 4,12Z">
                                </path>
                              </svg></span></span></button>
                      </div>
                      <div data-v-4ff6fa5e="">
                        <div class="v-dialog__container"></div>
                        <div data-v-35d8ec2b="">
                          <div data-v-35d8ec2b="" class="v-dialog__container"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div data-v-15230137="" data-v-15d6fcda="" class="mt-4">
                  <div data-v-15230137="" class="price-display-grid price-display-grid--split"> 
                    <div data-v-15230137="" style="grid-area: rate-nightly;">
                      <p data-v-15230137="" class="d-block mb-0"><span data-v-15230137=""
                          class="text-h8 font-weight-medium">
                          Rp
                        </span> <span data-v-15230137="" class="text-h5 font-weight-medium"
                          style="line-height: 1 !important;">
                          13,846,800
                        </span> <span data-v-15230137="" class="text-h8"> / night</span> <span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mt-n2 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span></p>
                    </div>
                    <div data-v-15230137="" style="grid-area: btn;"><button data-v-15230137="" type="button"
                        class="v-btn-choose my-1 v-btn v-btn--has-bg theme--light v-size--default primary"
                        style="opacity: 1;"><span class="v-btn__content">
                          Book Now
                        </span></button></div>
                    <div data-v-15230137="" style="grid-area: total-price;">
                      <p data-v-15230137="" class="mb-0 text-caption text-sm-body-2 text--secondary">
                        Total&nbsp;·&nbsp;Rp 55,387,200
                      </p>
                    </div>
                    <div data-v-15230137="" class="" style="grid-area: tax-fees;">
                      <p data-v-15230137="" class="mb-0 text-button text-sm-caption text--disabled">
                        after tax &amp; fees
                      </p>
                    </div>
                    <div data-v-15230137="" class="d-flex mt-1 flex-row align-baseline" style="grid-area: disclaimer;">
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center"><span data-v-15230137=""
                          aria-hidden="true" class="v-icon notranslate mr-1 text--disabled theme--light"
                          style="font-size: 8px; height: 8px; width: 8px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 8px; height: 8px; width: 8px;">
                            <path
                              d="M10,2H14L13.21,9.91L19.66,5.27L21.66,8.73L14.42,12L21.66,15.27L19.66,18.73L13.21,14.09L14,22H10L10.79,14.09L4.34,18.73L2.34,15.27L9.58,12L2.34,8.73L4.34,5.27L10.79,9.91L10,2Z">
                            </path>
                          </svg></span><span data-v-15230137=""
                          class="text-button text--disabled text-no-wrap">Member-only price, valid in app only</span>
                      </p> 
                      <div data-v-15230137="" class="spacer"></div>
                      <p data-v-15230137="" class="mb-0 d-flex justify-start align-center" style="gap: 4px;"><span
                          data-v-15230137="" aria-hidden="true" class="v-icon notranslate theme--light primary--text"
                          style="font-size: 12px; height: 12px; width: 12px;"><svg xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24" role="img" aria-hidden="true" class="v-icon__svg"
                            style="font-size: 12px; height: 12px; width: 12px;">
                            <path
                              d="M12,17.27L18.18,21L16.54,13.97L22,9.24L14.81,8.62L12,2L9.19,8.62L2,9.24L7.45,13.97L5.82,21L12,17.27Z">
                            </path>
                          </svg></span> <span data-v-15230137="" class="text-button primary--text">
                          Collect 12 points
                        </span></p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div data-v-15d6fcda="">
            <div class="v-dialog__container"></div>
          </div>
        </div>    
      </div>-->
    </div>
    <div class="v-dialog__container"></div>
    <div class="v-dialog__container"></div>
  </div>
</template>

<script>
import Tab from "@/components/stays/Tab.vue";

const defaultReviewGraph = {
  rating: 0,
  color: 'red',
  category: 'Bad'
};

export default {
  name: 'IndexPage',
  components: {
    Tab
  },
  data() {
    return {
      property: {
        catalog_data: {},
        review_graph: defaultReviewGraph
      },
      starRating: 0
    };
  },
  mounted() {
    this.fetchProperty();
  },
  methods: {
    async fetchProperty() {
      try {
        const response = await this.$axios.get('/property?id=9000248394&id=9000119804&id=9000119806&&include=important_info&include=image');
        this.property = response.data['9000248394'];
        this.starRating = this.property.catalog_data.star_rating;
        this.setReviewGraph();
      } catch (error) {
        console.error(error);
        this.property = {};
      }
    },
    getStarIcon(n) {
      if (n <= Math.floor(this.starRating)) {
        return "mdi-star";
      } else if (n === Math.ceil(this.starRating) && this.starRating % 1 !== 0) {
        return "mdi-star-half-full";
      }
      return "mdi-star-outline";
    },
    setReviewGraph() {
      this.property.review_graph = defaultReviewGraph;
      this.property.review_graph.rating = this.property.catalog_data.review_rating;
      if (this.property.catalog_data.review_rating >= 90) {
        this.property.review_graph.color = 'purple';
        this.property.review_graph.category = 'Excellent';
      } else if (this.property.catalog_data.review_rating >= 60) {
        this.property.review_graph.color = 'orange';
        this.property.review_graph.category = 'Average';
      }
    }
  }
}
</script>