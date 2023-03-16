<script setup>
import {RouterLink} from "vue-router";
import {ref, watch} from "vue";
import {useWindowsWidth} from "../../assets/js/useWindowsWidth";

// images
import ArrDark from "@/assets/img/down-arrow-dark.svg";
import downArrow from "@/assets/img/down-arrow.svg";
import DownArrWhite from "@/assets/img/down-arrow-white.svg";

const props = defineProps({
  action: {
    type: Object,
    route: String,
    color: String,
    label: String,
    default: () => ({
      route: "https://www.creative-tim.com/product/vue-material-kit",
      color: "bg-gradient-success",
      label: "Free Download"
    })
  },
  transparent: {
    type: Boolean,
    default: false
  },
  light: {
    type: Boolean,
    default: false
  },
  dark: {
    type: Boolean,
    default: false
  },
  sticky: {
    type: Boolean,
    default: false
  },
  darkText: {
    type: Boolean,
    default: false
  }
});

// set arrow  color
function getArrowColor() {
  if (props.transparent && textDark.value) {
    return ArrDark;
  } else if (props.transparent) {
    return DownArrWhite;
  } else {
    return ArrDark;
  }
}

// set text color
const getTextColor = () => {
  let color;
  if (props.transparent && textDark.value) {
    color = "text-dark";
  } else if (props.transparent) {
    color = "text-white";
  } else {
    color = "text-dark";
  }

  return color;
};

// set nav color on mobile && desktop

let textDark = ref(props.darkText);
const {type} = useWindowsWidth();

if (type.value === "mobile") {
  textDark.value = true;
} else if (type.value === "desktop" && textDark.value == false) {
  textDark.value = false;
}

watch(
    () => type.value,
    (newValue) => {
      if (newValue === "mobile") {
        textDark.value = true;
      } else {
        textDark.value = false;
      }
    }
);
</script>
<template>
  <nav
      class="navbar navbar-expand-lg top-0"
      :class="{
      'z-index-3 w-100 shadow-none navbar-transparent position-absolute my-3':
        props.transparent,
      'my-3 blur border-radius-lg z-index-3 py-2 shadow py-2 start-0 end-0 mx-4 position-absolute mt-4':
        props.sticky,
      'navbar-light bg-white py-3': props.light,
      ' navbar-dark bg-gradient-dark z-index-3 py-3': props.dark
    }"
  >
    <div
        :class="
        props.transparent || props.light || props.dark
          ? 'container'
          : 'container-fluid px-0'
      "
    >
      <RouterLink
          class="navbar-brand d-none d-md-block"
          :class="[
          (props.transparent && textDark.value) || !props.transparent
            ? 'text-dark font-weight-bolder ms-sm-3'
            : 'text-white font-weight-bolder ms-sm-3'
        ]"
          :to="{ name: 'presentation' }"
          rel="tooltip"
          title="The Digital Media Archive Collective"
          data-placement="bottom"
      >
        AntiochDAO
      </RouterLink>
      <RouterLink
          class="navbar-brand d-block d-md-none"
          :class="
          props.transparent || props.dark
            ? 'text-white'
            : 'font-weight-bolder ms-sm-3'
        "
          to="/"
          rel="tooltip"
          title="The Digital Media Archive Collective"
          data-placement="bottom"
      >
        Material Design
      </RouterLink>
      <a
          href="https://www.creative-tim.com/product/vue-material-kit-pro"
          class="btn btn-sm bg-gradient-success mb-0 ms-auto d-lg-none d-block"
      >Buy Now</a
      >
      <button
          class="navbar-toggler shadow-none ms-2"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navigation"
          aria-controls="navigation"
          aria-expanded="false"
          aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon mt-2">
          <span class="navbar-toggler-bar bar1"></span>
          <span class="navbar-toggler-bar bar2"></span>
          <span class="navbar-toggler-bar bar3"></span>
        </span>
      </button>
      <div
          class="collapse navbar-collapse w-100 pt-3 pb-2 py-lg-0"
          id="navigation"
      >
        <ul class="navbar-nav navbar-nav-hover ms-auto">
          <!--          <li class="nav-item dropdown dropdown-hover mx-2">-->
          <!--            <a-->
          <!--              role="button"-->
          <!--              class="nav-link ps-2 d-flex cursor-pointer align-items-center"-->
          <!--              :class="getTextColor()"-->
          <!--              id="dropdownMenuPages"-->
          <!--              data-bs-toggle="dropdown"-->
          <!--              aria-expanded="false"-->
          <!--            >-->
          <!--              <i-->
          <!--                class="material-icons opacity-6 me-2 text-md"-->
          <!--                :class="getTextColor()"-->
          <!--                >dashboard</i-->
          <!--              >-->
          <!--              Pages-->
          <!--              <img-->
          <!--                :src="getArrowColor()"-->
          <!--                alt="down-arrow"-->
          <!--                class="arrow ms-2 d-lg-block d-none"-->
          <!--              />-->
          <!--              <img-->
          <!--                :src="getArrowColor()"-->
          <!--                alt="down-arrow"-->
          <!--                class="arrow ms-1 d-lg-none d-block ms-auto"-->
          <!--              />-->
          <!--            </a>-->
          <!--            <div-->
          <!--              class="dropdown-menu dropdown-menu-animation ms-n3 dropdown-md p-3 border-radius-xl mt-0 mt-lg-3"-->
          <!--              aria-labelledby="dropdownMenuPages"-->
          <!--            >-->
          <!--              <div class="row d-none d-lg-block">-->
          <!--                <div class="col-12 px-4 py-2">-->
          <!--                  <div class="row">-->
          <!--                    <div class="position-relative">-->
          <!--                      <div-->
          <!--                        class="dropdown-header text-dark font-weight-bolder d-flex align-items-center px-1"-->
          <!--                      >-->
          <!--                        Landing Pages-->
          <!--                      </div>-->
          <!--                      <RouterLink-->
          <!--                        :to="{ name: 'about' }"-->
          <!--                        class="dropdown-item border-radius-md"-->
          <!--                      >-->
          <!--                        <span>About Us</span>-->
          <!--                      </RouterLink>-->
          <!--                      <RouterLink-->
          <!--                        :to="{ name: 'contactus' }"-->
          <!--                        class="dropdown-item border-radius-md"-->
          <!--                      >-->
          <!--                        <span>Contact Us</span>-->
          <!--                      </RouterLink>-->
          <!--                      <RouterLink-->
          <!--                        :to="{ name: 'author' }"-->
          <!--                        class="dropdown-item border-radius-md"-->
          <!--                      >-->
          <!--                        <span>Author</span>-->
          <!--                      </RouterLink>-->
          <!--                      <div-->
          <!--                        class="dropdown-header text-dark font-weight-bolder d-flex align-items-center px-0 mt-3"-->
          <!--                      >-->
          <!--                        Account-->
          <!--                      </div>-->
          <!--                      <RouterLink-->
          <!--                        :to="{ name: 'signin-basic' }"-->
          <!--                        class="dropdown-item border-radius-md"-->
          <!--                      >-->
          <!--                        <span>Sign In</span>-->
          <!--                      </RouterLink>-->
          <!--                    </div>-->
          <!--                  </div>-->
          <!--                </div>-->
          <!--              </div>-->
          <!--              <div class="d-lg-none">-->
          <!--                <div-->
          <!--                  class="dropdown-header text-dark font-weight-bolder d-flex align-items-center px-0"-->
          <!--                >-->
          <!--                  Landing Pages-->
          <!--                </div>-->
          <!--                <RouterLink-->
          <!--                  :to="{ name: 'about' }"-->
          <!--                  class="dropdown-item border-radius-md"-->
          <!--                >-->
          <!--                  <span>About Us</span>-->
          <!--                </RouterLink>-->
          <!--                <RouterLink-->
          <!--                  :to="{ name: 'contactus' }"-->
          <!--                  class="dropdown-item border-radius-md"-->
          <!--                >-->
          <!--                  <span>Contact Us</span>-->
          <!--                </RouterLink>-->
          <!--                <RouterLink-->
          <!--                  :to="{ name: 'author' }"-->
          <!--                  class="dropdown-item border-radius-md"-->
          <!--                >-->
          <!--                  <span>Author</span>-->
          <!--                </RouterLink>-->
          <!--                <div-->
          <!--                  class="dropdown-header text-dark font-weight-bolder d-flex align-items-center px-0 mt-3"-->
          <!--                >-->
          <!--                  Account-->
          <!--                </div>-->
          <!--                <RouterLink-->
          <!--                  :to="{ name: 'signin-basic' }"-->
          <!--                  class="dropdown-item border-radius-md"-->
          <!--                >-->
          <!--                  <span>Sign In</span>-->
          <!--                </RouterLink>-->
          <!--              </div>-->
          <!--            </div>-->
          <!--          </li>-->
          <!--          <li class="nav-item dropdown dropdown-hover mx-2">-->
          <!--            <a-->
          <!--              role="button"-->
          <!--              class="nav-link ps-2 d-flex cursor-pointer align-items-center"-->
          <!--              :class="getTextColor()"-->
          <!--              id="dropdownMenuBlocks"-->
          <!--              data-bs-toggle="dropdown"-->
          <!--              aria-expanded="false"-->
          <!--            >-->
          <!--              <i-->
          <!--                class="material-icons opacity-6 me-2 text-md"-->
          <!--                :class="getTextColor()"-->
          <!--                >view_day</i-->
          <!--              >-->
          <!--              Sections-->
          <!--              <img-->
          <!--                :src="getArrowColor()"-->
          <!--                alt="down-arrow"-->
          <!--                class="arrow ms-2 d-lg-block d-none"-->
          <!--              />-->
          <!--              <img-->
          <!--                :src="getArrowColor()"-->
          <!--                alt="down-arrow"-->
          <!--                class="arrow ms-1 d-lg-none d-block ms-auto"-->
          <!--              />-->
          <!--            </a>-->
          <!--            <div-->
          <!--              class="dropdown-menu dropdown-menu-end dropdown-menu-animation dropdown-md dropdown-md-responsive p-3 border-radius-lg mt-0 mt-lg-3"-->
          <!--              aria-labelledby="dropdownMenuBlocks"-->
          <!--            >-->
          <!--              <div class="d-none d-lg-block">-->
          <!--                <ul class="list-group">-->
          <!--                  <li-->
          <!--                    class="nav-item dropdown dropdown-hover dropdown-subitem list-group-item border-0 p-0"-->
          <!--                  >-->
          <!--                    <a-->
          <!--                      class="dropdown-item py-2 ps-3 border-radius-md"-->
          <!--                      href="javascript:;"-->
          <!--                    >-->
          <!--                      <div class="d-flex">-->
          <!--                        <div-->
          <!--                          class="w-100 d-flex align-items-center justify-content-between"-->
          <!--                        >-->
          <!--                          <div>-->
          <!--                            <h6-->
          <!--                              class="dropdown-header text-dark font-weight-bolder d-flex justify-content-cente align-items-center p-0"-->
          <!--                            >-->
          <!--                              Page Sections-->
          <!--                            </h6>-->
          <!--                            <span class="text-sm">See all sections</span>-->
          <!--                          </div>-->
          <!--                          <img-->
          <!--                            :src="downArrow"-->
          <!--                            alt="down-arrow"-->
          <!--                            class="arrow"-->
          <!--                          />-->
          <!--                        </div>-->
          <!--                      </div>-->
          <!--                    </a>-->
          <!--                    <div class="dropdown-menu mt-0 py-3 px-2 mt-3">-->
          <!--                      <RouterLink-->
          <!--                        class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                        :to="{ name: 'page-headers' }"-->
          <!--                      >-->
          <!--                        Page Headers-->
          <!--                      </RouterLink>-->
          <!--                      <RouterLink-->
          <!--                        class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                        :to="{ name: 'page-features' }"-->
          <!--                      >-->
          <!--                        Features-->
          <!--                      </RouterLink>-->
          <!--                    </div>-->
          <!--                  </li>-->
          <!--                  <li-->
          <!--                    class="nav-item dropdown dropdown-hover dropdown-subitem list-group-item border-0 p-0"-->
          <!--                  >-->
          <!--                    <a-->
          <!--                      class="dropdown-item py-2 ps-3 border-radius-md"-->
          <!--                      href="javascript:;"-->
          <!--                    >-->
          <!--                      <div class="d-flex">-->
          <!--                        <div-->
          <!--                          class="w-100 d-flex align-items-center justify-content-between"-->
          <!--                        >-->
          <!--                          <div>-->
          <!--                            <h6-->
          <!--                              class="dropdown-header text-dark font-weight-bolder d-flex justify-content-cente align-items-center p-0"-->
          <!--                            >-->
          <!--                              Navigation-->
          <!--                            </h6>-->
          <!--                            <span class="text-sm">See all navigations</span>-->
          <!--                          </div>-->
          <!--                          <img-->
          <!--                            :src="downArrow"-->
          <!--                            alt="down-arrow"-->
          <!--                            class="arrow"-->
          <!--                          />-->
          <!--                        </div>-->
          <!--                      </div>-->
          <!--                    </a>-->
          <!--                    <div class="dropdown-menu mt-0 py-3 px-2 mt-3">-->
          <!--                      <RouterLink-->
          <!--                        class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                        :to="{ name: 'navigation-navbars' }"-->
          <!--                      >-->
          <!--                        Navbars-->
          <!--                      </RouterLink>-->
          <!--                      <RouterLink-->
          <!--                        class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                        :to="{ name: 'navigation-navtabs' }"-->
          <!--                      >-->
          <!--                        Nav Tabs-->
          <!--                      </RouterLink>-->
          <!--                      <RouterLink-->
          <!--                        class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                        :to="{ name: 'navigation-pagination' }"-->
          <!--                      >-->
          <!--                        Pagination-->
          <!--                      </RouterLink>-->
          <!--                    </div>-->
          <!--                  </li>-->
          <!--                  <li-->
          <!--                    class="nav-item dropdown dropdown-hover dropdown-subitem list-group-item border-0 p-0"-->
          <!--                  >-->
          <!--                    <a-->
          <!--                      class="dropdown-item py-2 ps-3 border-radius-md"-->
          <!--                      href="javascript:;"-->
          <!--                    >-->
          <!--                      <div class="d-flex">-->
          <!--                        <div-->
          <!--                          class="w-100 d-flex align-items-center justify-content-between"-->
          <!--                        >-->
          <!--                          <div>-->
          <!--                            <h6-->
          <!--                              class="dropdown-header text-dark font-weight-bolder d-flex justify-content-cente align-items-center p-0"-->
          <!--                            >-->
          <!--                              Input Areas-->
          <!--                            </h6>-->
          <!--                            <span class="text-sm">See all input areas</span>-->
          <!--                          </div>-->
          <!--                          <img-->
          <!--                            :src="downArrow"-->
          <!--                            alt="down-arrow"-->
          <!--                            class="arrow"-->
          <!--                          />-->
          <!--                        </div>-->
          <!--                      </div>-->
          <!--                    </a>-->
          <!--                    <div class="dropdown-menu mt-0 py-3 px-2 mt-3">-->
          <!--                      <RouterLink-->
          <!--                        class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                        :to="{ name: 'inputareas-inputs' }"-->
          <!--                      >-->
          <!--                        Inputs-->
          <!--                      </RouterLink>-->
          <!--                      <RouterLink-->
          <!--                        class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                        :to="{ name: 'inputareas-forms' }"-->
          <!--                      >-->
          <!--                        Forms-->
          <!--                      </RouterLink>-->
          <!--                    </div>-->
          <!--                  </li>-->
          <!--                  <li-->
          <!--                    class="nav-item dropdown dropdown-hover dropdown-subitem list-group-item border-0 p-0"-->
          <!--                  >-->
          <!--                    <a-->
          <!--                      class="dropdown-item py-2 ps-3 border-radius-md"-->
          <!--                      href="javascript:;"-->
          <!--                    >-->
          <!--                      <div class="d-flex">-->
          <!--                        <div-->
          <!--                          class="w-100 d-flex align-items-center justify-content-between"-->
          <!--                        >-->
          <!--                          <div>-->
          <!--                            <h6-->
          <!--                              class="dropdown-header text-dark font-weight-bolder d-flex justify-content-cente align-items-center p-0"-->
          <!--                            >-->
          <!--                              Attention Catchers-->
          <!--                            </h6>-->
          <!--                            <span class="text-sm">See all examples</span>-->
          <!--                          </div>-->
          <!--                          <img-->
          <!--                            :src="downArrow"-->
          <!--                            alt="down-arrow"-->
          <!--                            class="arrow"-->
          <!--                          />-->
          <!--                        </div>-->
          <!--                      </div>-->
          <!--                    </a>-->
          <!--                    <div class="dropdown-menu mt-0 py-3 px-2 mt-3">-->
          <!--                      <RouterLink-->
          <!--                        class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                        :to="{ name: 'ac-alerts' }"-->
          <!--                      >-->
          <!--                        Alerts-->
          <!--                      </RouterLink>-->
          <!--                      <RouterLink-->
          <!--                        class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                        :to="{ name: 'ac-modals' }"-->
          <!--                      >-->
          <!--                        Modals-->
          <!--                      </RouterLink>-->
          <!--                      <RouterLink-->
          <!--                        class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                        :to="{ name: 'ac-tooltips-popovers' }"-->
          <!--                      >-->
          <!--                        Tooltips & Popovers-->
          <!--                      </RouterLink>-->
          <!--                    </div>-->
          <!--                  </li>-->
          <!--                  <li-->
          <!--                    class="nav-item dropdown dropdown-hover dropdown-subitem list-group-item border-0 p-0"-->
          <!--                  >-->
          <!--                    <a-->
          <!--                      class="dropdown-item py-2 ps-3 border-radius-md"-->
          <!--                      href="javascript:;"-->
          <!--                    >-->
          <!--                      <div class="d-flex">-->
          <!--                        <div-->
          <!--                          class="w-100 d-flex align-items-center justify-content-between"-->
          <!--                        >-->
          <!--                          <div>-->
          <!--                            <h6-->
          <!--                              class="dropdown-header text-dark font-weight-bolder d-flex justify-content-cente align-items-center p-0"-->
          <!--                            >-->
          <!--                              Elements-->
          <!--                            </h6>-->
          <!--                            <span class="text-sm">See all elements</span>-->
          <!--                          </div>-->
          <!--                          <img-->
          <!--                            :src="downArrow"-->
          <!--                            alt="down-arrow"-->
          <!--                            class="arrow"-->
          <!--                          />-->
          <!--                        </div>-->
          <!--                      </div>-->
          <!--                    </a>-->
          <!--                    <div class="dropdown-menu mt-0 py-3 px-2 mt-3">-->
          <!--                      <RouterLink-->
          <!--                        class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                        :to="{ name: 'el-avatars' }"-->
          <!--                      >-->
          <!--                        Avatars-->
          <!--                      </RouterLink>-->
          <!--                      <RouterLink-->
          <!--                        class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                        :to="{ name: 'el-badges' }"-->
          <!--                      >-->
          <!--                        Badges-->
          <!--                      </RouterLink>-->
          <!--                      <RouterLink-->
          <!--                        class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                        :to="{ name: 'el-breadcrumbs' }"-->
          <!--                      >-->
          <!--                        Breadcrumbs-->
          <!--                      </RouterLink>-->
          <!--                      <RouterLink-->
          <!--                        class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                        :to="{ name: 'el-buttons' }"-->
          <!--                      >-->
          <!--                        Buttons-->
          <!--                      </RouterLink>-->
          <!--                      <RouterLink-->
          <!--                        class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                        :to="{ name: 'el-button-groups' }"-->
          <!--                      >-->
          <!--                        Button Groups-->
          <!--                      </RouterLink>-->
          <!--                      <RouterLink-->
          <!--                        class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                        :to="{ name: 'el-dropdowns' }"-->
          <!--                      >-->
          <!--                        Dropdowns-->
          <!--                      </RouterLink>-->
          <!--                      <RouterLink-->
          <!--                        class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                        :to="{ name: 'el-progress-bars' }"-->
          <!--                      >-->
          <!--                        Progress Bars-->
          <!--                      </RouterLink>-->
          <!--                      <RouterLink-->
          <!--                        class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                        :to="{ name: 'el-toggles' }"-->
          <!--                      >-->
          <!--                        Toggles-->
          <!--                      </RouterLink>-->
          <!--                      <RouterLink-->
          <!--                        class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                        :to="{ name: 'el-typography' }"-->
          <!--                      >-->
          <!--                        Typography-->
          <!--                      </RouterLink>-->
          <!--                    </div>-->
          <!--                  </li>-->
          <!--                </ul>-->
          <!--              </div>-->
          <!--              <div class="row d-lg-none">-->
          <!--                <div class="col-md-12">-->
          <!--                  <div class="d-flex mb-2">-->
          <!--                    <div-->
          <!--                      class="w-100 d-flex align-items-center justify-content-between"-->
          <!--                    >-->
          <!--                      <div>-->
          <!--                        <h6-->
          <!--                          class="dropdown-header text-dark font-weight-bolder d-flex justify-content-cente align-items-center p-0"-->
          <!--                        >-->
          <!--                          Page Sections-->
          <!--                        </h6>-->
          <!--                      </div>-->
          <!--                    </div>-->
          <!--                  </div>-->
          <!--                  <RouterLink-->
          <!--                    class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                    :to="{ name: 'page-headers' }"-->
          <!--                  >-->
          <!--                    Page Headers-->
          <!--                  </RouterLink>-->
          <!--                  <RouterLink-->
          <!--                    class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                    :to="{ name: 'page-features' }"-->
          <!--                  >-->
          <!--                    Features-->
          <!--                  </RouterLink>-->
          <!--                  <div class="d-flex mb-2 mt-3">-->
          <!--                    <div-->
          <!--                      class="w-100 d-flex align-items-center justify-content-between"-->
          <!--                    >-->
          <!--                      <div>-->
          <!--                        <h6-->
          <!--                          class="dropdown-header text-dark font-weight-bolder d-flex justify-content-cente align-items-center p-0"-->
          <!--                        >-->
          <!--                          Navigation-->
          <!--                        </h6>-->
          <!--                      </div>-->
          <!--                    </div>-->
          <!--                  </div>-->
          <!--                  <RouterLink-->
          <!--                    class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                    :to="{ name: 'navigation-navbars' }"-->
          <!--                  >-->
          <!--                    Navbars-->
          <!--                  </RouterLink>-->
          <!--                  <RouterLink-->
          <!--                    class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                    :to="{ name: 'navigation-navtabs' }"-->
          <!--                  >-->
          <!--                    Nav Tabs-->
          <!--                  </RouterLink>-->
          <!--                  <RouterLink-->
          <!--                    class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                    :to="{ name: 'navigation-pagination' }"-->
          <!--                  >-->
          <!--                    Pagination-->
          <!--                  </RouterLink>-->
          <!--                  <div class="d-flex mb-2 mt-3">-->
          <!--                    <div-->
          <!--                      class="w-100 d-flex align-items-center justify-content-between"-->
          <!--                    >-->
          <!--                      <div>-->
          <!--                        <h6-->
          <!--                          class="dropdown-header text-dark font-weight-bolder d-flex justify-content-cente align-items-center p-0"-->
          <!--                        >-->
          <!--                          Input Areas-->
          <!--                        </h6>-->
          <!--                      </div>-->
          <!--                    </div>-->
          <!--                  </div>-->
          <!--                  <RouterLink-->
          <!--                    class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                    :to="{ name: 'inputareas-inputs' }"-->
          <!--                  >-->
          <!--                    Inputs-->
          <!--                  </RouterLink>-->
          <!--                  <RouterLink-->
          <!--                    class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                    :to="{ name: 'inputareas-forms' }"-->
          <!--                  >-->
          <!--                    Forms-->
          <!--                  </RouterLink>-->
          <!--                  <div class="d-flex mb-2 mt-3">-->
          <!--                    <div-->
          <!--                      class="w-100 d-flex align-items-center justify-content-between"-->
          <!--                    >-->
          <!--                      <div>-->
          <!--                        <h6-->
          <!--                          class="dropdown-header text-dark font-weight-bolder d-flex justify-content-cente align-items-center p-0"-->
          <!--                        >-->
          <!--                          Attention Catchers-->
          <!--                        </h6>-->
          <!--                      </div>-->
          <!--                    </div>-->
          <!--                  </div>-->
          <!--                  <RouterLink-->
          <!--                    class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                    :to="{ name: 'ac-alerts' }"-->
          <!--                  >-->
          <!--                    Alerts-->
          <!--                  </RouterLink>-->
          <!--                  <RouterLink-->
          <!--                    class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                    :to="{ name: 'ac-modals' }"-->
          <!--                  >-->
          <!--                    Modals-->
          <!--                  </RouterLink>-->
          <!--                  <RouterLink-->
          <!--                    class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                    :to="{ name: 'ac-tooltips-popovers' }"-->
          <!--                  >-->
          <!--                    Tooltips & Popovers-->
          <!--                  </RouterLink>-->
          <!--                  <div class="d-flex mb-2 mt-3">-->
          <!--                    <div-->
          <!--                      class="w-100 d-flex align-items-center justify-content-between"-->
          <!--                    >-->
          <!--                      <div>-->
          <!--                        <h6-->
          <!--                          class="dropdown-header text-dark font-weight-bolder d-flex justify-content-cente align-items-center p-0"-->
          <!--                        >-->
          <!--                          Elements-->
          <!--                        </h6>-->
          <!--                      </div>-->
          <!--                    </div>-->
          <!--                  </div>-->
          <!--                  <RouterLink-->
          <!--                    class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                    :to="{ name: 'el-avatars' }"-->
          <!--                  >-->
          <!--                    Avatars-->
          <!--                  </RouterLink>-->
          <!--                  <RouterLink-->
          <!--                    class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                    :to="{ name: 'el-badges' }"-->
          <!--                  >-->
          <!--                    Badges-->
          <!--                  </RouterLink>-->
          <!--                  <RouterLink-->
          <!--                    class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                    :to="{ name: 'el-breadcrumbs' }"-->
          <!--                  >-->
          <!--                    Breadcrumbs-->
          <!--                  </RouterLink>-->
          <!--                  <RouterLink-->
          <!--                    class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                    :to="{ name: 'el-buttons' }"-->
          <!--                  >-->
          <!--                    Buttons-->
          <!--                  </RouterLink>-->
          <!--                  <RouterLink-->
          <!--                    class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                    :to="{ name: 'el-button-groups' }"-->
          <!--                  >-->
          <!--                    Button Groups-->
          <!--                  </RouterLink>-->
          <!--                  <RouterLink-->
          <!--                    class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                    :to="{ name: 'el-dropdowns' }"-->
          <!--                  >-->
          <!--                    Dropdowns-->
          <!--                  </RouterLink>-->
          <!--                  <RouterLink-->
          <!--                    class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                    :to="{ name: 'el-progress-bars' }"-->
          <!--                  >-->
          <!--                    Progress Bars-->
          <!--                  </RouterLink>-->
          <!--                  <RouterLink-->
          <!--                    class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                    :to="{ name: 'el-toggles' }"-->
          <!--                  >-->
          <!--                    Toggles-->
          <!--                  </RouterLink>-->
          <!--                  <RouterLink-->
          <!--                    class="dropdown-item ps-3 border-radius-md mb-1"-->
          <!--                    :to="{ name: 'el-typography' }"-->
          <!--                  >-->
          <!--                    Typography-->
          <!--                  </RouterLink>-->
          <!--                </div>-->
          <!--              </div>-->
          <!--            </div>-->
          <!--          </li>-->
          <!--          <li class="nav-item dropdown dropdown-hover mx-2">-->
          <!--            <a-->
          <!--              role="button"-->
          <!--              class="nav-link ps-2 d-flex cursor-pointer align-items-center"-->
          <!--              :class="getTextColor()"-->
          <!--              id="dropdownMenuDocs"-->
          <!--              data-bs-toggle="dropdown"-->
          <!--              aria-expanded="false"-->
          <!--            >-->
          <!--              <i-->
          <!--                class="material-icons opacity-6 me-2 text-md"-->
          <!--                :class="getTextColor()"-->
          <!--                >article</i-->
          <!--              >-->
          <!--              Docs-->
          <!--              <img-->
          <!--                :src="getArrowColor()"-->
          <!--                alt="down-arrow"-->
          <!--                class="arrow ms-2 d-lg-block d-none"-->
          <!--              />-->
          <!--              <img-->
          <!--                :src="getArrowColor()"-->
          <!--                alt="down-arrow"-->
          <!--                class="arrow ms-1 d-lg-none d-block ms-auto"-->
          <!--              />-->
          <!--            </a>-->
          <!--            <div-->
          <!--              class="dropdown-menu dropdown-menu-end dropdown-menu-animation dropdown-md mt-0 mt-lg-3 p-3 border-radius-lg"-->
          <!--              aria-labelledby="dropdownMenuDocs"-->
          <!--            >-->
          <!--              <div class="d-none d-lg-block">-->
          <!--                <ul class="list-group">-->
          <!--                  <li class="nav-item list-group-item border-0 p-0">-->
          <!--                    <a-->
          <!--                      class="dropdown-item py-2 ps-3 border-radius-md"-->
          <!--                      href=" https://www.creative-tim.com/learning-lab/vue/overview/material-kit/"-->
          <!--                    >-->
          <!--                      <h6-->
          <!--                        class="dropdown-header text-dark font-weight-bolder d-flex justify-content-cente align-items-center p-0"-->
          <!--                      >-->
          <!--                        Getting Started-->
          <!--                      </h6>-->
          <!--                      <span class="text-sm"-->
          <!--                        >All about overview, quick start, license and-->
          <!--                        contents</span-->
          <!--                      >-->
          <!--                    </a>-->
          <!--                  </li>-->
          <!--                  <li class="nav-item list-group-item border-0 p-0">-->
          <!--                    <a-->
          <!--                      class="dropdown-item py-2 ps-3 border-radius-md"-->
          <!--                      href=" https://www.creative-tim.com/learning-lab/vue/colors/material-kit/"-->
          <!--                    >-->
          <!--                      <h6-->
          <!--                        class="dropdown-header text-dark font-weight-bolder d-flex justify-content-cente align-items-center p-0"-->
          <!--                      >-->
          <!--                        Foundation-->
          <!--                      </h6>-->
          <!--                      <span class="text-sm"-->
          <!--                        >See our colors, icons and typography</span-->
          <!--                      >-->
          <!--                    </a>-->
          <!--                  </li>-->
          <!--                  <li class="nav-item list-group-item border-0 p-0">-->
          <!--                    <a-->
          <!--                      class="dropdown-item py-2 ps-3 border-radius-md"-->
          <!--                      href=" https://www.creative-tim.com/learning-lab/vue/alerts/material-kit/"-->
          <!--                    >-->
          <!--                      <h6-->
          <!--                        class="dropdown-header text-dark font-weight-bolder d-flex justify-content-cente align-items-center p-0"-->
          <!--                      >-->
          <!--                        Components-->
          <!--                      </h6>-->
          <!--                      <span class="text-sm"-->
          <!--                        >Explore our collection of fully designed-->
          <!--                        components</span-->
          <!--                      >-->
          <!--                    </a>-->
          <!--                  </li>-->
          <!--                </ul>-->
          <!--              </div>-->
          <!--              <div class="row d-lg-none">-->
          <!--                <div class="col-md-12 g-0">-->
          <!--                  <a-->
          <!--                    class="dropdown-item py-2 ps-3 border-radius-md"-->
          <!--                    href="./pages/about-us.html"-->
          <!--                  >-->
          <!--                    <h6-->
          <!--                      class="dropdown-header text-dark font-weight-bolder d-flex justify-content-cente align-items-center p-0"-->
          <!--                    >-->
          <!--                      Getting Started-->
          <!--                    </h6>-->
          <!--                    <span class="text-sm"-->
          <!--                      >All about overview, quick start, license and-->
          <!--                      contents</span-->
          <!--                    >-->
          <!--                  </a>-->
          <!--                  <a-->
          <!--                    class="dropdown-item py-2 ps-3 border-radius-md"-->
          <!--                    href="./pages/about-us.html"-->
          <!--                  >-->
          <!--                    <h6-->
          <!--                      class="dropdown-header text-dark font-weight-bolder d-flex justify-content-cente align-items-center p-0"-->
          <!--                    >-->
          <!--                      Foundation-->
          <!--                    </h6>-->
          <!--                    <span class="text-sm"-->
          <!--                      >See our colors, icons and typography</span-->
          <!--                    >-->
          <!--                  </a>-->
          <!--                  <a-->
          <!--                    class="dropdown-item py-2 ps-3 border-radius-md"-->
          <!--                    href="./pages/about-us.html"-->
          <!--                  >-->
          <!--                    <h6-->
          <!--                      class="dropdown-header text-dark font-weight-bolder d-flex justify-content-cente align-items-center p-0"-->
          <!--                    >-->
          <!--                      Components-->
          <!--                    </h6>-->
          <!--                    <span class="text-sm"-->
          <!--                      >Explore our collection of fully designed components</span-->
          <!--                    >-->
          <!--                  </a>-->
          <!--                  <a-->
          <!--                    class="dropdown-item py-2 ps-3 border-radius-md"-->
          <!--                    href="./pages/about-us.html"-->
          <!--                  >-->
          <!--                    <h6-->
          <!--                      class="dropdown-header text-dark font-weight-bolder d-flex justify-content-cente align-items-center p-0"-->
          <!--                    >-->
          <!--                      Plugins-->
          <!--                    </h6>-->
          <!--                    <span class="text-sm"-->
          <!--                      >Check how you can integrate our plugins</span-->
          <!--                    >-->
          <!--                  </a>-->
          <!--                  <a-->
          <!--                    class="dropdown-item py-2 ps-3 border-radius-md"-->
          <!--                    href="./pages/about-us.html"-->
          <!--                  >-->
          <!--                    <h6-->
          <!--                      class="dropdown-header text-dark font-weight-bolder d-flex justify-content-cente align-items-center p-0"-->
          <!--                    >-->
          <!--                      Utility Classes-->
          <!--                    </h6>-->
          <!--                    <span class="text-sm"-->
          <!--                      >For those who want flexibility, use our utility-->
          <!--                      classes</span-->
          <!--                    >-->
          <!--                  </a>-->
          <!--                </div>-->
          <!--              </div>-->
          <!--            </div>-->
          <!--          </li>-->
          <li class="nav-item dropdown dropdown-hover mx-2">
            <a
                href="https://github.com/orgs/AntiochDAO/repositories"
                class="nav-link d-flex cursor-pointer align-items-center"
                target="_blank"
            >
              <svg
                  width="20px"
                  height="20px"
                  class="material-icons me-2 opacity-6"
                  viewBox="0 0 24 24"
                  aria-hidden="true"
                  data-testid="GitHubIcon"
                  :fill="props.transparent && '#fff'"
              >
                <path
                    d="M12 1.27a11 11 0 00-3.48 21.46c.55.09.73-.28.73-.55v-1.84c-3.03.64-3.67-1.46-3.67-1.46-.55-1.29-1.28-1.65-1.28-1.65-.92-.65.1-.65.1-.65 1.1 0 1.73 1.1 1.73 1.1.92 1.65 2.57 1.2 3.21.92a2 2 0 01.64-1.47c-2.47-.27-5.04-1.19-5.04-5.5 0-1.1.46-2.1 1.2-2.84a3.76 3.76 0 010-2.93s.91-.28 3.11 1.1c1.8-.49 3.7-.49 5.5 0 2.1-1.38 3.02-1.1 3.02-1.1a3.76 3.76 0 010 2.93c.83.74 1.2 1.74 1.2 2.94 0 4.21-2.57 5.13-5.04 5.4.45.37.82.92.82 2.02v3.03c0 .27.1.64.73.55A11 11 0 0012 1.27"
                ></path>
              </svg>
              Github
            </a>
          </li>
          <li class="nav-item dropdown dropdown-hover mx-2">
            <a
                href="https://ethglobal.com/showcase/antiochdao-o2yow"
                class="nav-link d-flex cursor-pointer align-items-center"
                target="_blank"
            >
              <svg
                  width="20"
                  height="20"
                  viewBox="0 0 241 241"
                  fill="none"
                  xmlns="http://www.w3.org/2000/svg"
                  class="material-icons me-2 opacity-6"
              >
                <path fill-rule="evenodd" clip-rule="evenodd"
                      d="M225.632 15.373c-22.258-22.264-62.823-19.604-105.09 3.191-6.311 3.397-5.839 17.351.137 21.003a248.3 248.3 0 0 1 80.72 80.863c3.632 5.98 17.745 6.185 21.042.061a194.957 194.957 0 0 0-2.396-4.324c.817 1.439 1.616 2.88 2.396 4.323 22.79-42.277 25.448-82.854 3.191-105.117Zm-47.038 47.05a263.74 263.74 0 0 0-39.547-32.689c16.363-7.569 31.95-11.626 45.153-11.626 11.805 0 21.711 3.238 28.578 10.107 14.57 14.573 12.838 42.779-1.504 73.766a266.286 266.286 0 0 0-32.68-39.558Z"
                      fill="#FFC750"></path>
                <path fill-rule="evenodd" clip-rule="evenodd"
                      d="M235.446 151.095a175.874 175.874 0 0 0-13.027-30.494c-3.344-6.218-17.43-6.031-21.053-.061a240.808 240.808 0 0 1-35.677 45.165 240.491 240.491 0 0 1-45.086 35.709c-5.979 3.653-6.247 17.726-.136 21.009C142.979 234.57 165.005 241 184.052 241c16.721 0 31.147-4.955 41.559-15.37 16.296-16.296 19.777-42.762 9.835-74.535Zm-22.695 61.675c-14.577 14.578-42.775 12.83-73.77-1.52a263.834 263.834 0 0 0 39.568-32.7 265.546 265.546 0 0 0 32.712-39.509c14.335 30.981 16.068 59.165 1.49 73.729Z"
                      fill="#FF6895"></path>
                <path fill-rule="evenodd" clip-rule="evenodd"
                      d="M120.378 18.58A174.81 174.81 0 0 0 89.873 5.552c-31.751-9.94-58.213-6.46-74.507 9.834C4.955 25.8 0 40.224 0 56.943c0 19.046 6.43 41.084 18.558 63.595 3.299 6.111 17.37 5.835 21.021-.152a248.102 248.102 0 0 1 80.936-80.8c5.941-3.612 6.065-17.678-.137-21.007Zm-90.633 83.43c-14.348-30.992-16.096-59.203-1.52-73.779 11.263-11.263 31.235-13.163 56.222-5.32a148.821 148.821 0 0 1 17.54 6.795 272.405 272.405 0 0 0-72.242 72.304Z"
                      fill="#5FC5A6"></path>
                <path fill-rule="evenodd" clip-rule="evenodd"
                      d="M120.973 201.408a241.042 241.042 0 0 1-45.4-35.702 240.382 240.382 0 0 1-35.835-45.231c-3.636-5.935-17.758-6.049-21.098.152a175.337 175.337 0 0 0-13.06 30.472c-9.991 31.766-6.482 58.227 9.856 74.519C25.688 235.817 39.936 241 56.992 241a112.09 112.09 0 0 0 33.226-5.563 177.037 177.037 0 0 0 30.617-13.025c4.928-2.629 6.094-17.383.138-21.004Zm-36.201 16.687c-25.08 7.827-45.126 5.927-56.43-5.335-11.304-11.262-13.211-31.233-5.354-56.219a147.372 147.372 0 0 1 6.819-17.524 266.397 266.397 0 0 0 32.875 39.532 264.292 264.292 0 0 0 39.694 32.737 147.298 147.298 0 0 1-17.604 6.809Z"
                      fill="#5666F6"></path>
                <path fill-rule="evenodd" clip-rule="evenodd" d="M80 119.799 120.5 56l40.5 63.799L120.5 143 80 119.799Z"
                      fill="#1F294F"></path>
                <path fill-rule="evenodd" clip-rule="evenodd" d="m80 130 40.5 23.157L161 130l-40.5 55L80 130Z"
                      fill="#1F294F"></path>
                <path fill-rule="evenodd" clip-rule="evenodd"
                      d="M139 30.169A191.112 191.112 0 0 0 120.576 40 180.262 180.262 0 0 0 102 30.123 214.501 214.501 0 0 1 120.439 19 220.649 220.649 0 0 1 139 30.169Z"
                      fill="#5F9A34"></path>
                <path fill-rule="evenodd" clip-rule="evenodd"
                      d="M222 120.538A219.324 219.324 0 0 1 210.871 139 192.085 192.085 0 0 0 201 120.477 194.499 194.499 0 0 0 210.856 102 223.556 223.556 0 0 1 222 120.538Z"
                      fill="#FF512F"></path>
                <path fill-rule="evenodd" clip-rule="evenodd"
                      d="M139 210.831c-1.28.867-2.56 1.702-3.84 2.523A213.69 213.69 0 0 1 120.439 222c-6.126-3.282-12.272-6.99-18.439-11.123A180.457 180.457 0 0 0 120.576 201 184.758 184.758 0 0 0 139 210.831Z"
                      fill="#552990"></path>
                <path fill-rule="evenodd" clip-rule="evenodd"
                      d="M40 120.416c-3.647 6-6.947 12.205-9.885 18.584A222.655 222.655 0 0 1 19 120.569 218.653 218.653 0 0 1 30.176 102 184.59 184.59 0 0 0 40 120.416Z"
                      fill="#204FA0"></path>
              </svg>
              Scaling Ethereum Showcase
            </a>
          </li>
        </ul>
        <!--        <ul class="navbar-nav d-lg-block d-none">-->
        <!--          <li class="nav-item">-->
        <!--            <a-->
        <!--              :href="action.route"-->
        <!--              class="btn btn-sm mb-0"-->
        <!--              :class="action.color"-->
        <!--              onclick="smoothToPricing('pricing-soft-ui')"-->
        <!--              >{{ action.label }}</a-->
        <!--            >-->
        <!--          </li>-->
        <!--        </ul>-->
      </div>
    </div>
  </nav>
  <!-- End Navbar -->
</template>
