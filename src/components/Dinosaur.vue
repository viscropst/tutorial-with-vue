<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    props: { dinosaur: String },
    data(): ComponentData {
        return {
            dinosaurDetails: null
        };
    },
    async mounted() {
        const res = await fetch(`/api/dinosaurs/${this.dinosaur}`);
        this.dinosaurDetails = await res.json();
    }
});
</script>

<template>
    <h1>{{ dinosaurDetails?.name }}</h1>
    <p>{{ dinosaurDetails?.description }}</p>
    <RouterLink to="/" class="btn btn-secondary">Back to all dinosaurs</RouterLink>
</template>
