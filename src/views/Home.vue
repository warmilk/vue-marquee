<template>
    <div class="home">
       <marquee></marquee>
    </div>
</template>

<script>
    // @ is an alias to /src
    import marquee from '@/components/marquee.vue'
    export default {
        name: 'Home',
        components: {
            marquee
        }
    }
</script>
