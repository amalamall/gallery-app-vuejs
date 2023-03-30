<template>
  <div class="home">
    <SectionDisplay />
    <ListImages />
  </div>
</template>

<script>
// @ is an alias to /src
import SectionDisplay from "@/components/SectionDisplay.vue";
import ListImages from "@/components/ListImages.vue"

export default {
  name: "HomeView",
  components: {
    SectionDisplay,
    ListImages
  },
}
</script>
