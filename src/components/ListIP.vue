<template>
    <div>

        <ul>

            <ItemIP
                    v-for="(dataIp, i) of dataIp"
                    :dataIp="dataIp"
                    v-bind:key="dataIp"
                    v-bind:index="i"
                    v-on:remove-dataIp="removeDataIP"
            />
        </ul>

    </div>
</template>

<script>
    import ItemIP from '@/components/ItemIP'
    export default {
        props: ['dataIp'],

        components: {
            ItemIP
        },
        methods:{
            removeDataIP(id){

                this.$emit('remove-dataIp', id)
            }
    }
    }
</script>