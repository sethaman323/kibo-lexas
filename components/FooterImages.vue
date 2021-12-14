<template>
  <div>
     
    <FooterImagesSection
      v-for="section in page.sections"
      :key="section.id"
      :section="section"
    />
  </div>
</template>

<script>
import FooterImagesSection from './contentpage/Section';

export default {
  components: {
    FooterImagesSection
  },

  props: {
    page: {
      type: Object,
      required: true
    }
  }
}
</script>
