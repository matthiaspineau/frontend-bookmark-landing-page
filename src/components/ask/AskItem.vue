<template>
    <div class="ask" @click="emitAnswer(file.id)" :data-id="file.id">
        <div class="ask__top">
            <h3 class="ask__title">{{ file.title }}</h3>
            <div class="ask__media">
                <img :src="require('@/assets/image/'+file.img+'.svg')" alt="">
            </div>
        </div>
        <div class="ask__text">{{ file.description }}</div>
    </div>
</template>

<script>
export default {
    name: 'AskItem',
    props: {
        file: {
            type: Object,
            default() {
                return {}
            }
        }
    },
    methods: {
        emitAnswer(id) {
        this.$emit("emit-answer", { message: id});
        },
    }
}
</script>