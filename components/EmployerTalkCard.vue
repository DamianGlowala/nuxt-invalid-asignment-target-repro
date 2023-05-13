<template>
    <div
        class="rounded-lg bg-gradient-to-br from-primary-tint-40 to-tertiary-tint-40 p-1 shadow-lg"
    >
        <div class="flex h-full flex-col overflow-hidden rounded">
            <div
                class="relative flex grow flex-col border-t border-gray-100 bg-white p-4 before:absolute before:inset-x-0 before:-mt-4 before:h-8 before:-translate-y-full before:bg-gradient-to-t before:from-black/5 before:to-transparent"
            >
                <template v-if="isYouTubeVideoUrl">
                    <button
                        class="button-tertiary mt-8 flex items-center justify-center space-x-1.5"
                        @click="isWatchYouTubeEmployerTalkVideoModalOpen = true"
                    >
                        <Icon name="mdi:youtube" class="flex-none text-xl" />

                        <span class="text-center">Watch recording</span>
                    </button>

                    <WatchYouTubeEmployerTalkVideoModal
                        v-model:is-open="
                            isWatchYouTubeEmployerTalkVideoModalOpen
                        "
                        :title="event.headline"
                        :video-url="event.videoUrl"
                    />
                </template>

                <NuxtLink
                    v-else
                    :to="event.videoUrl"
                    target="_blank"
                    class="button-tertiary mt-8 flex items-center justify-center space-x-1.5"
                >
                    <span class="text-center">Open recording</span>

                    <Icon name="mdi:open-in-new" class="flex-none text-xs" />
                </NuxtLink>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
export type Props = {
    event: {
        headline: string;
        videoUrl: string;
    };
};

const props = defineProps<Props>();

const isWatchYouTubeEmployerTalkVideoModalOpen = ref(false);

const isYouTubeVideoUrl = computed(() =>
    props.event.videoUrl.match(
        /^(?:https?:\/\/)?(?:m\.|www\.)?(?:youtu\.be\/|youtube\.com\/(?:embed\/|v\/|watch\?v=|watch\?.+&v=))((\w|-){11})(?:\S+)?$/
    )
);
</script>
