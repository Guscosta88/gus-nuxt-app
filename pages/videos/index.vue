<template>
    <div>
        <nuxt-child />
        <h1>Videos</h1>
        <div v-for="video in $store.state.videos" :key="video.id"> 
        <nuxt-link :to="`/videos/${video.id}`">{{ video.name }}</nuxt-link>
        </div>
        
    </div>
    
</template>
<script>
export default {
    head: {
        title:'Gus-Nuxt-App - Video List'
    },
    async fetch({$axios, store}) {
        let response = await $axios.get('/videos')
        let videos = response.data.data.map(v => v.attributes);

      
        store.commit('SET_VIDEOS', videos);
        // return { videos


            // videos: 
            
            // [{
            //     id: '16',
            //     name: 'Intro to NuxtJS'
            // },
            // {
            //     id: '1',
            //     name: 'Intro to VueJS'
            // },
            // {
            //     id: '71',
            //     name: 'Advanced Techniques for Library X'
            // }]


        // }
    },
}
</script>
<style lang="scss" scoped>
    
</style>