<template>
  <v-app>
    <v-main>
      <Appbar/>
      <Insert/>
    </v-main>
  </v-app>
</template>

<script>
import Insert from './views/Insert';
import Appbar from './components/Appbar';


export default {
  name: 'App',

  components: {
    Appbar,
    Insert,
  },

  data: () => ({
    //
  }),
};
</script>
