<template>
  <base-card>
    <base-button
      @click="setSelectedTab('stored-resources')"
      :mode="storedResourceButtonMode"
      >Stored Resources</base-button
    >
    <base-button
      @click="setSelectedTab('add-resources')"
      :mode="addResourceButtonMode"
      >Add Resources</base-button
    >
  </base-card>
  <!-- keep alive caches memory of the component so for eg the form fields will not reset when we switch components or data in component wont reset -->
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
  <!-- ^^^ instead of using component(which is dynamic component ) u can alos use v-if here and than u dont need to use provide/inject in scripts -->
</template>

<script>
import StoredResources from "./StoredResources.vue";
import AddResources from "./AddResources.vue";
export default {
  components: {
    AddResources,
    StoredResources,
  },
  data() {
    return {
      selectedTab: "stored-resources",
      storedResources: [
        {
          id: "official-documentation",
          title: "Official Guide",
          description: " The official Vue.js docs",
          link: "https://vuejs.org",
        },
        {
          id: "google",
          title: "Google",
          description: "Larn Everything",
          link: "https://google.com",
        },
      ],
    };
  },

  provide() {
    return {
      storedResources: this.storedResources,
      addResource: this.addResource,
      removeResouse: this.removeResouse,
    };
  },
  computed: {
    storedResourceButtonMode() {
      console.log("called 1");
      return this.selectedTab === "stored-resources" ? null : "flat";
    },
    addResourceButtonMode() {
      console.log("called 2");
      return this.selectedTab === "add-resources" ? null : "flat";
    },
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, description, link) {
      const newResource = {
        id: new Date().toISOString(),
        title,
        description,
        link,
      };
      this.storedResources.unshift(newResource);
      this.selectedTab = "stored-resources";
    },
    removeResouse(resId) {
      // if we do it like this the issue is that we are creating a new array, vue doesnt recognize that and doest make any chage
      //   const temp = this.storedResources.filter((res) => res.id !== resId);
      //   this.storedResources = temp;
      // so we need to make changed to origial array only
      const indexOfToBeRemoved = this.storedResources
        .map((e) => e.id)
        .indexOf(resId);
      this.storedResources.splice(indexOfToBeRemoved, 1);
    },
  },
};
</script>
