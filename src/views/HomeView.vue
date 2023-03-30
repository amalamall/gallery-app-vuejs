<template>
  <div>
    <SectionDisplay />
    <ListImages />
  </div>
</template>

<script>
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
