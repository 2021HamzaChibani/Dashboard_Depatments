<template>
    <Link
        v-if="href"
        :href="href"
        class="px-3 py-2 mr-2 rounded text-white text-sm font-bold whitespace-no-wrap"
        :class="classes"
    >
        <slot />
    </Link>
    <button
        v-else
        class="px-3 py-2 mr-2 rounded text-white text-sm font-bold whitespace-no-wrap"
        :class="classes"
    >
        <slot />
    </button>
</template>

<script>
import {Link} from "@inertiajs/inertia-vue3";
import Button from "@/Components/Button";
export default {
    name: "AnchorLink",
    components:{
        Button,
        Link
    },
    props:{
        href:String,
        mode:{
            type:String,
            default: 'add'
        }
    },
    computed:{
         classes(){
             if(this.mode == 'add'){
                 return 'bg-blue-600 hover:bg-blue-800';
             }
             if(this.mode == 'edit'){
                 return 'bg-yellow-600 hover:bg-blue-800';
             }
             if(this.mode == 'delete'){
                 return 'bg-red-600 hover:bg-blue-800';
             }
             if(this.mode == 'view'){
                 return 'bg-green-600 hover:bg-blue-800';
             }
             return '';
         }
    }

}
</script>

<style scoped>

</style>
