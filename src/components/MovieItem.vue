<template>
    <li>
      {{ title }} - {{ year }}
    </li>
  </template>
  
  <script>
  export default {
    props: {
      title: String,
      year: Number,
    },
  };
  </script>