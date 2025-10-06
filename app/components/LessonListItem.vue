<script setup lang="ts">
    const props = defineProps<{
        lesson: { number: number; title: string; duration: string }
    }>()

    
    const playlistSlug = useRoute().params.playlistSlug
    const lessonSlug = props.lesson.title.toLowerCase().replaceAll(' ', '-') //Получаем слаг для адреса урока, все буквы маленькие и пробелы заменяем на тире
    const linkClasses = computed(() =>['flex items-center justify-between w-full p-3 text-indigo-700 rounded-lg gap-x-4 dark:text-gray-300 dark:hover:bg-gray-700',
            useRoute().params.lessonSlug === lessonSlug
            ? 'bg-indigo-50 text-indigo-700 dark:bg-gray-700' // active classes
            : 'text-gray-600 hover:bg-gray-100' //inactiv classes
    ])
            

</script>
<template>
    <li>
        <NuxtLink 
            :to="`/playlists/${playlistSlug}/lessons/${lessonSlug}`"
            :class="linkClasses">
        <span class="text-sm font-medium truncate sm:text-base">
            {{ lesson.number }}. {{ lesson.title }}
        </span>
        <span class="text-sm text-gray-500 sm:text-base">
            {{ lesson.duration }}
        </span>
        </NuxtLink>
    </li>
</template>