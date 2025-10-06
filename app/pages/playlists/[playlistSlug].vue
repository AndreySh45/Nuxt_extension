<script setup lang="ts">
  const playlist = usePlaylistsStore().getPlaylistBySlug(
            useRoute().params.playlistSlug,
        )
</script>

<template>
    <section class="flex flex-col pt-24 pb-12 gap-y-8 sm:py-16 md:gap-y-12">
      <AppSectionHeader
          type="page"
          :heading="playlist.title"
          :subheading="playlist.description"
      />
      <div class="container grid grid-cols-1 gap-y-8 lg:gap-x-8 lg:grid-cols-3">
        <PlaylistLessons />
        <NuxtPage />
      </div>
    </section>
</template>