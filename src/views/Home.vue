

<template>
    <div class="home">
       <marquee :joinList="joinList"></marquee>
    </div>
</template>

<script>
    // @ is an alias to /src
    /* eslint-disable no-console */

    import marquee from '@/components/marquee.vue'
    export default {
        data() {
            return {
                joinList: [
                    {
                        avatar: require('@/assets/logo.png'),
                        nickname: '顶顶顶'
                    },
                    {
                        avatar: require('@/assets/logo.png'),
                        nickname: '顶顶顶'
                    },
                    {
                        avatar: require('@/assets/logo.png'),
                        nickname: '顶顶顶'
                    },
                    {
                        avatar: require('@/assets/logo.png'),
                        nickname: '顶顶顶'
                    },
                    {
                        avatar: require('@/assets/logo.png'),
                        nickname: '顶顶顶'
                    },
                    {
                        avatar: require('@/assets/logo.png'),
                        nickname: '顶顶顶'
                    },
                    {
                        avatar: require('@/assets/logo.png'),
                        nickname: '顶顶顶'
                    },

                ]
            }
        },
        name: 'Home',
        components: {
            marquee
        }
    }
</script>
