<script setup lang="ts">
    defineOptions({ inheritAttrs: false }) //отмена стандартного наследования атрибутов
    defineProps<{ id: string }>()
</script>

<template>
    <div class="flex flex-col gap-y-1">
        <AppLabel v-if="$slots.default" :for="id"> <!-- проверка - передан ли текст в стандартом слоте -->
            <slot />
        </AppLabel>
        <AppInput :id="id" v-bind="$attrs" />
    </div>
</template>