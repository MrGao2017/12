<template>
    <div>
        欢迎来到人员管理系统
        <fotter-nav :class="{'isIndex':'!isNowPage'}"></fotter-nav>
    </div>
</template>

<script>
    import FotterNav from '@/components/fotter.vue'
    export default {
        components:{
            FotterNav
        },
        data(){
            return {
                isNowPage:true
            }
        }
    }
</script>