<template>
    <div class="flex flex-wrap -m-4 items-end">
        <div v-for="(i, index) in illustrations" :key="index" class="p-4 w-1/2">
            <img class="w-full" :src="path + i.pathShort" />
            <div class="mt-3 mb-8">
                <a :href="path + i.pathShort" target="_blank"><button class="px-4 py-2 bg-primary-500 hover:bg-primary-600 transition-all duration-200 text-white rounded mr-1">Download .SVG</button></a>
                <!-- <a href="/assets/logo-primary.png" target="_blank"><button class="px-4 py-2 bg-primary-500 hover:bg-primary-600 transition-all duration-200 text-white rounded">Download .SVG</button></a> -->
            </div>
            <br />
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            path: "/assets/illustrations/",
            illustrations: [],
        }
    },
    mounted() {
        this.importAll(require.context('../../static/assets/illustrations/', true, /\.svg$/));
    },
    methods: {
        importAll(r) {
            r.keys().forEach(key => (this.illustrations.push({ pathLong: r(key), pathShort: key })));
        },
    },
}
</script>

<style>

</style>