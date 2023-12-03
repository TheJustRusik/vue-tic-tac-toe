<script setup>
    defineProps({
        msg : {
            type: String,
            required: true
        }
    })
</script>

<template>
    <button @click="$emit('clicked')" class="transition ease-in-out hover:-translate-y-1 hover:scale-110 rounded-xl hover:bg-sky-500 transition duration-300 ease-in-out bg-pink-500">
        <div>
            <p class="text-white text-2xl font-extrabold p-4">{{ msg }}</p>
        </div>
    </button>
</template>