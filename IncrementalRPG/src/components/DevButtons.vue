<template>
    <div v-if="isDevMode">
        <button onclick="saveGame()">Save</button>
        <button @click="clearLocalStorage">Clear Local Storage</button>
        <button @click="maxEverything">Max Everything</button>
        <button @click="upStorage">Up Storage</button>
    </div>
</template>

<script>
export default {
    name: 'DevButtons',
    props: {
        isDevMode: {
            type: Boolean,
            required: true
        }
    },
    methods: {
        clearLocalStorage() {
            localStorage.clear();
            window.location.reload();
        },
        maxEverything() {
            for (r in resource) {
                let obj = eval(resource[r]);
                obj.total = obj.max;
            }
        },
        upStorage() {
            for (r in resource) {
                let obj = eval(resource[r]);
                obj.max *= 2;
            }
        }
    }
}
</script>