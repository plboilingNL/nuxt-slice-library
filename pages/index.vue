<!--
Looking for more information about the Slice Zone? Here's the documentation about it:
https://www.slicemachine.dev/documentation/nuxt/add-the-slice-zone-to-your-page
-->
<template>
  <div>
    <slice-zone type="header" uid="header" :theme="theme"></slice-zone>
    <slice-zone type="page" uid="home" />
    <slice-zone type="footer" uid="footer" :theme="theme"></slice-zone>
  </div>
</template>

<script>
  import SliceZone from "vue-slicezone";

  export default {
    components: {
      SliceZone
    },
    head() {
      const {
        meta_title,
        meta_description,
        social_cards : [{
          social_card_image,
          social_card_title,
          social_card_description
        }]} = this.data;

      return {
        title: meta_title,
        meta: [{
          hid: "description",
          name: "description",
          content: meta_description
        },
        {
          hid: "twitter:image",
          name: "twitter:image",
          content: social_card_image.url
        },
        {
          hid: "twitter:title",
          name: "twitter:title",
          content: social_card_title
        },
        {
          hid: "twitter:description",
          name: "twitter:description",
          content: social_card_description
        },
        {
          hid: "og:image",
          name: "og:image",
          content: social_card_image.url
        },
        {
          hid: "og:title",
          name: "og:title",
          content: social_card_title
        },
        {
          hid: "og:description",
          name: "og:description",
          content: social_card_description
        },
        {
          hid: "twitter:image",
          name: "twitter:image",
          content: "@iexistin3d"
        },
        ]
      }
    },
    data: {
      theme: {
        hero_text_color: null, /* TW class name */
        navBar: {
          ctaColor: null, /* TW class name */
        },
        eyebrow: {
          color: null /* TW class name */
        },
        title: null, /* TW class name */
        description: null, /* TW class name */
        featureTitle: null, /* TW class name */
        featureDescription: null, /* TW class name */
        footer_container: null, /* TW class name */
        footer_image: null, /* TW class name */
        copyNoticeBg: null, /* TW class name */
      }
    },
    async asyncData(context) {
      const data = (await context.$prismic.api.getByUID("page", "home")).data;

      return { data };
    },
  }

</script>
