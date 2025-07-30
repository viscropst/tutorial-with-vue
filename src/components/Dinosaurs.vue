<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    async setup() {
        const res = await fetch("/api/dinosaurs")
        const dinosaurs = await res.json() as Dinosaur[];
        return { dinosaurs };
    }
});
</script>

<template>
    <span v-for="dinosaur in dinosaurs" :key="dinosaur.name">
        <RouterLink :to="{ name: 'Dinosaur', params: { dinosaur: `${dinosaur.name.toLowerCase()}` } }"
            class="btn btn-primary">
            {{ dinosaur.name }}
        </RouterLink>
    </span>
</template>
