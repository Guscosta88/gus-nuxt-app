<template>
    <div>
        <nuxt-child :video="video"/>
    </div>
</template>
<script>
import { mapState } from 'vuex';
export default {
    head() {
        return{
            title: '',
        titleTemplate: `%s ${this.video.name} - Gus Videos`
        }
    },
    async fetch({$axios, params, store}) {
        let response = await $axios.get(`/videos/${params.id}`)
        let video = response.data.data.attributes;

        store.commit('SET_CURRENT_VIDEO', video);

    },
    computed: {
        ...mapState({
            video: 'currentVideo'
        })
    }
}



        // return {
        //     video

    //         videos: [{
    //             id: '16',
    //             name: 'Intro to NuxtJS'
    //         },
    //         {
    //             id: '1',
    //             name: 'Intro to VueJS'
    //         },
    //         {
    //             id: '71',
    //             name: 'Advanced Techniques for Library X'
    //         }]
    //     }
    // },
    // computed: {
    //     video() {
    //         return this.videos.find(v => v.id == this.$route.params.id)
    //     }

    // }
    
    

</script>
<style lang="scss" scoped>
    
</style>