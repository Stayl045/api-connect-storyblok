<template>
  <section v-if="data">
    <!-- <pre>{{ data }}</pre> -->
    <h1
      class="grid text-center gap-4 bg-purple-300 py-4 justify-items-center mb-5"
    >
      {{ data.title }}
    </h1>
    <p class="mb-5 py-4 mx-5">{{ data.description }}</p>
    <img :src="data.image" alt="" class="w-full h-1/2 mb-5" />
    <footer>
      <p>&copy; Stephan, Taylor 2022</p>
    </footer>
  </section>
</template>

<script setup>
  import { ref, onMounted } from "vue";

  const data = ref(null);

  onMounted(async () => {
    data.value = await fetch(
      "https://api.storyblok.com/v1/cdn/stories/landing-page?version=draft&token=QR8ahDmJ4nkA4AaSKCZBdQtt&cv=1648444111"
    )
      .then((response) => response.json())
      .then(({ story }) => story.content);
  });
</script>
