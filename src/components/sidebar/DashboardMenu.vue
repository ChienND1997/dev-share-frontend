<template>
  <span v-for="element in menuElements" :key="element.menu">
    <NuxtLink :to="element.path">
      <li class="relative px-6 py-3 hover:bg-[rgba( 59, 73, 223 , 0.1))]" @click="closeMobileSideMenu(), toggleSelectedElement(element)">
        <span
          v-if="element.isActive"
          class="absolute inset-y-0 left-0 w-1 bg-purple-600 rounded-tr-lg rounded-br-lg"
          aria-hidden="true"
        ></span>
        <span
          class="inline-flex items-center w-full text-sm font-semibold transition-colors duration-150 hover:text-gray-800 dark:hover:text-gray-200 hover:underline"
          :class="{
            'text-gray-800 dark:text-gray-100': element.isActive,
          }"
        >
          <Icon :name="element.icon" size="1.5rem" />
          <span class="ml-4">{{ $utils.stringUtils.toUcFirst(element.menu) }}</span>
        </span>
      </li>
    </NuxtLink>
  </span>
</template>

<script lang="ts">
import { useLayoutStore } from "@/stores/LayoutStore";

type MenuElement = {
  menu: string;
  isActive: boolean;
  svgPaths: string[];
};

export default defineComponent({
  mounted() {
    const menu = this.menuElements.find((element) => this.menuRoot + element.menu === String(this.$route.path));
    if (menu) {
      this.toggleSelectedElement(menu);
    } else {
      this.toggleSelectedElement(this.menuElements[0]);
    }
  },
  data() {
    return {
      menuElements: [
        {
          menu: "home",
          icon: "i-cif:vn",
          path: "/",
          isActive: false,
        },
        {
          menu: "Reading List",
          icon: "i-openmoji-radio",
          path: "/",
          isActive: false,
        },
        {
          menu: "Postcasts",
          icon: "i-twemoji-studio-microphone",
          path: "/",
          isActive: false,
        },
        {
          menu: "Videos",
          icon: "i-openmoji-film-projector",
          path: "/",
          isActive: false,
        },
        {
          menu: "Tags",
          icon: "i-noto-label",
          path: "/",
          isActive: false,
        },
        {
          menu: "FAQ",
          icon: "i-twemoji-light-bulb",
          path: "/",
          isActive: false,
        },
        {
          menu: "About",
          icon: "i-fluent-emoji-flat-open-book",
          path: "/",
          isActive: false,
        },
      ],
      activeLink: false,
    };
  },
  methods: {
    ...mapActions(useLayoutStore, ["closeMobileSideMenu"]),
    toggleSelectedElement(menuElement: MenuElement): void {
      this.menuElements.forEach((menu) => {
        menu.isActive = false;
      });
      menuElement.isActive = true;
    },
  },
});
</script>
