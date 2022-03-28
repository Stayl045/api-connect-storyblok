<template>
  <div v-if="data">
    <h1>{{ data.title }}</h1>
    <p>{{ data.description }}</p>
    <img :src="data.image.filename" alt="Image of Howl" class="w-3/6 h-1/2" />
  </div>
</template>

<script setup>
  import { ref, onMounted } from "vue";

  const data = ref(null);

  onMounted(async () => {
    data.value = await fetch(
      "https://api.storyblok.com/v1/cdn/stories/landing-page?version=draft&token=QR8ahDmJ4nkA4AaSKCZBdQtt&cv=1648427023"
    )
      .then((response) => response.json())
      .then(({ story }) => story.content);
  });
</script>
