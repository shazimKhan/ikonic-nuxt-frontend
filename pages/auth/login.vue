<template>
    <b-container id="mainContainer" align-v="center">
      <BlobBg />
      <b-row align-v="center" align-h="center">
        <b-col md="6">
          <FormLogin />
        </b-col>
        <b-col md="6">
          <b-img
            :src="require('@/assets/images/business.png')"
            fluid
            class="businessImg scale-in-bottom"
            center
          />
        </b-col>
      </b-row>
    </b-container>
  </template>
  
  <script>
  import FormLogin from '@/components/Auth/FormLogin';
  import BlobBg from '@/components/Auth/BlobBg';
  
  export default {
    components: {
      FormLogin,
      BlobBg
    },
  };
  </script>
  
  <style lang="scss">
  #mainContainer {
    width: 100%;
    height: auto;
    position: relative;
  }
  </style>