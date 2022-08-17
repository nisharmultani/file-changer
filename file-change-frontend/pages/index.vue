<template>
  <div>ok {{ this.size() }}</div>
</template>

<script>
import imagemin from "imagemin";
import pngToJpeg from "png-to-jpeg";
import sizeOf from "image-size";
export default {
  methods: {
    size() {
      imagemin(["images/*.png"], "build/images", {
        plugins: [pngToJpeg({ quality: 90 })],
      }).then((files) => {
        // Please keep in mind that all files now have the wrong extension
        // You might want to change them manually
        console.log("PNGs converted to JPEGs:", files);
      });
    },
  },
};
</script>
