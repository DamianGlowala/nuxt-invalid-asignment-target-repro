<template>
    <div></div>
</template>

<script setup lang="ts">
export type Props = {
    isOpen: boolean;
    title: string;
    videoUrl: string;
};

defineProps<Props>();

const emit = defineEmits<{
    (e: "update:isOpen", isOpen: boolean): void;
}>();

function closeModal() {
    emit("update:isOpen", false);
}
</script>
