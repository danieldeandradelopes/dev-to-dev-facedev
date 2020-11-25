<template>
  <q-layout view="lHh Lpr lFf">
    <q-header class="row items-center justify-between q-mt-sm">
      <q-img width="130px" class="q-mx-sm q-my-md" src="../assets/logo.png">
      </q-img>
      <div>
        <q-icon
          name="fas fa-search"
          class="q-mx-sm q-pa-sm q-icon-custom"
          size="25px"
          color="black"
        ></q-icon>
        <q-icon
          name="fab fa-facebook-messenger"
          class="q-mx-sm q-pa-sm q-icon-custom"
          size="25px"
          color="black"
        ></q-icon>
      </div>

      <!-- <q-icon
          name="fas fa-bars"
          class="q-mx-sm q-pa-sm"
          size="30px"
          color="black"
          @click="leftDrawerOpen = !leftDrawerOpen"
        ></q-icon> -->
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-1"
    >
      <q-list>
        <q-item-label header class="text-grey-8">
          Essential Links
        </q-item-label>
        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from "components/EssentialLink.vue";
const linksData = [
  {
    title: "Docs",
    caption: "quasar.dev",
    icon: "school",
    link: "https://quasar.dev",
  },
  {
    title: "Github",
    caption: "github.com/quasarframework",
    icon: "code",
    link: "https://github.com/quasarframework",
  },
  {
    title: "Discord Chat Channel",
    caption: "chat.quasar.dev",
    icon: "chat",
    link: "https://chat.quasar.dev",
  },
  {
    title: "Forum",
    caption: "forum.quasar.dev",
    icon: "record_voice_over",
    link: "https://forum.quasar.dev",
  },
  {
    title: "Twitter",
    caption: "@quasarframework",
    icon: "rss_feed",
    link: "https://twitter.quasar.dev",
  },
  {
    title: "Facebook",
    caption: "@QuasarFramework",
    icon: "public",
    link: "https://facebook.quasar.dev",
  },
  {
    title: "Quasar Awesome",
    caption: "Community Quasar projects",
    icon: "favorite",
    link: "https://awesome.quasar.dev",
  },
];

export default {
  name: "MainLayout",
  components: { EssentialLink },
  data() {
    return {
      leftDrawerOpen: false,
      essentialLinks: linksData,
      tab: "mails",
    };
  },
};
</script>


<style lang="scss" scoped>
.q-icon-custom {
  background-color: #f2f3f7;
  border-radius: 50%;
}
</style>

