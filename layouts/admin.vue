<template>
  <div class="flex h-screen">
    <NavSidebar :isSidebarActive="isSidebarActive">
      <template #items>
        <li>
          <NuxtLink
            to="/admin"
            class="inline-flex items-center w-full px-4 py-2 mt-1 space-x-2 text-base transition duration-200 ease-in-out transform bg-black border rounded-lg text-stone-400 border-stone-700 hover:bg-stone-700 focus:shadow-outline "
          >
            <IconGridAlt />
            <span> Dashboard</span>
          </NuxtLink>
        </li>
        
      </template>
      <template #footer>
        <a
          @click.prevent="signOut"
          href="#"
          class="flex-shrink-0 w-full text-stone-400 group"
        >
          <div class="flex items-center">
            <IconLogOut />
            <div class="ml-3">
              <div class="text-xs text-stone-500">
                {{ userCookie.email }}
              </div>
              <p class="text-sm font-medium text-neutral-200">Sign out</p>
            </div>
          </div>
        </a>
      </template>
    </NavSidebar>

    <div
      class="w-full h-screen mx-auto overflow-y-scroll dark:bg-zinc-800 bg-stone-300 "
    >
      <!-- Main Content -->
      <slot />
    </div>
  </div>
</template>

<script setup>
import {
  IconGridAlt,
  IconTrash,
  IconBook,
  IconMenu,
  IconX,
  IconLogOut,
  IconCube,
  IconPlus
} from "@iconify-prerendered/vue-bx";
const isSidebarActive = ref(false);
const router = useRouter();

const userCookie = useCookie("userCookie");

const signOut = async () => {
  // console.log("signing out");
  await signOutUser();
  router.push("/admin/signin");
};
</script>

<style>
/* home route and active route will show in bold as it matches / and /about */
/* .nuxt-link-active {
    font-weight: bold;
} */
.router-link-active {
  font-weight: bold;
  color: #16928a;
  text-decoration: none;
}
/* a.router-link-active {
  font-weight: bold;
  color: #059669;
  text-decoration: none;
} */
/* exact link will show the primary color for only the exact matching link */
/* a.router-link-exact-active {
  font-weight: bold;
} */
/* exact link will show the primary color for only the exact matching link */
/* a.router-link-hover {
  color: #e1d13c;
} */
</style>

