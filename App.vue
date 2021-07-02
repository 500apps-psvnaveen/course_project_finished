<template>
  <the-header title="Remember Me"></the-header>
  <the-resources></the-resources>
</template>

<script>
import TheHeader from './components/layouts/TheHeader.vue';
import TheResources from './components/learning-resources/TheResources.vue';

// import LearningResources from './components/learning-resources/LearningResources.vue';

export default {
  components: {
    TheHeader,
    TheResources,
  },
  //   components: {
  //     LearningResources,
  //   },
  data() {
    return {
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
  methods: {
    // addingResources(id, title, description, link) {
    //   const addNewResource = {
    //     id: id,
    //     title: title,
    //     description: description,
    //     link: link,
    //   };
    //   this.storedResources.push(addNewResource);
    // },
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>