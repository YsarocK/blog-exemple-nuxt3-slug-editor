<template>
  <div class="flex flex-col gap-1 w-fit">
    <label class="font-medium text-xs text-slate-500">URL</label>
    <div class="bg-slate-100 border-none rounded-md px-4 py-3 text-sm flex">
      <p class="text-slate-400">http://localhost:3000/</p>
      <div class="relative">
        <label for="" class="w-full px-1 pointer-events-none">{{ slug }}</label>
        <input
          ref="slugInput"
          @change="handleSlug"
          class="absolute top-0 left-0 w-full px-1 text-transparent caret-green-500 bg-transparent border-none text-sm outline-none"
          type="text"
          contenteditable
          v-model="slug"
        />
      </div>
      <p class="text-slate-400">/your-album-name</p>
    </div>
  </div>
</template>

<script setup lang="ts">
import slugify from "slugify";

const slug = ref("etienne");
const slugInput = ref();
const handleSlug = () => {
  const normalizedSlug = slugify((slugInput.value as HTMLInputElement).value, {
    lower: true,
  });
  slug.value = normalizedSlug;
};
</script>
