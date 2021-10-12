<template>
  <div>
    <header>
      <!-- Meter Nav Bar -->
      <TheHeader></TheHeader>
    </header>
    <nuxt />
  </div>
</template>

<script>
import TheHeader from "@/components/TheHeader"
export default {
   components: {
     TheHeader
   }
};
</script>