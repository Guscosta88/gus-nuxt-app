<template>
    <div>
        <nuxt-child />
        <h1>Videos</h1>
        <div v-for="video in videos" :key="video.id"> 
        <nuxt-link :to="`/videos/${video.id}`">{{ video.name }}</nuxt-link>
        </div>
        
    </div>
    
</template>
<script>
export default {
    async asyncData(context) {
        let response = await context.$axios.get('http://localhost:3000/api/videos')

        console.log(response);
        debugger

        return {
            videos: [{
                id: '16',
                name: 'Intro to NuxtJS'
            },
            {
                id: '1',
                name: 'Intro to VueJS'
            },
            {
                id: '71',
                name: 'Advanced Techniques for Library X'
            }]
        }
    },
}
</script>
<style lang="scss" scoped>
    
</style>