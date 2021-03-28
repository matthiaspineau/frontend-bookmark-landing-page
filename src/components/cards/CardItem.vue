<template>
    <div class="card">
        <div class="card__media">
            <img :src="require('@/assets/image/'+file.img+'.svg')" alt="">
        </div>
        <div class="card__text">
            <h3 class="card__text__title">{{ file.title }}</h3>
            <span class="card__text__p">{{ file.description }}</span>
        </div>
        <div class="card__separator">
            <img :src="require('@/assets/image/bg-dots.svg')" alt="">
        </div>
        <button class="btn btn__blue__plain">{{ file.button }}</button>
    </div>
</template>

<script>
export default {
    name: 'CardItem',
    props: {
        file: {
            type: Object,
            default() {
                return {}
            }
        },
    }
}
</script>