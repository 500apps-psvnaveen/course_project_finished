<template>
  <base-card>
    <base-button
      @click="resourcesFunction('stored-resources')"
      :mode="storedResourcesCheck"
    >
      Stored Resources
    </base-button>
    <base-button
      @click="resourcesFunction('add-resources')"
      :mode="addResourcesCheck"
      >Add Resources</base-button
    >
  </base-card>
  <!-- <add-resources></add-resources>
    <stored-resources></stored-resources> -->
  <!-- <component :is="resourcesValue"></component> -->
  <!-- <add-resources v-if="resourcesValue === 'add-resources'" ></add-resources>
  <stored-resources v-if="resourcesValue === 'stored-resources'" ><stored-resources> -->
  <keep-alive>
    <component :is="resourcesValue"></component>
  </keep-alive>
</template>

<script>
import AddResources from './AddResources.vue';
import StoredResources from './StoredResources.vue';

export default {
  components: {
    AddResources,
    StoredResources,
  },

  data() {
    return {
      resourcesValue: 'stored-resources',
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The official vue.js documentation.',
          link: 'https://vuejs.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to Google...',
          link: 'https://google.org',
        },
        {
          id: 'python',
          title: 'Python',
          description: 'Learn Python',
          link: 'https://python.org',
        },
      ],
    };
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
      deleteResource: this.removeResource,
    };
  },
  computed: {
    storedResourcesCheck() {
      return this.resourcesValue === 'stored-resources' ? null : 'flat';
    },
    addResourcesCheck() {
      return this.resourcesValue === 'add-resources' ? null : 'flat';
    },
  },
  methods: {
    resourcesFunction(res) {
      this.resourcesValue = res;
    },
    addResource(title, description, url) {
      const newResource = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: url,
      };
      this.storedResources.unshift(newResource);
      this.resourcesValue = 'stored-resources';
    },
    removeResource(resId) {
      this.storedResources = this.storedResources.filter(
        (res) => res.id != resId
      );
    },
  },
};
</script>