<template>
<div>
    <Link :href="route('home')">Home</Link>
    This another page
</div>
</template>

<script>
import { Link } from '@inertiajs/inertia-vue3'

export default {
    name: "Another",
    components:{
        Link
    }
}
</script>

<style scoped>

</style>
