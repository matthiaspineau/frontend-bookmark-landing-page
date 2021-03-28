<template>
    <div>
        <div v-for="(item, index) in file" 
        :key="item.idTab"
        :data-id="item.idTab"
        :class="[index == 0 ? 'visible' : '']"
        class="t-tab">
            <div class="t-tab__media">
                <img :src="require('@/assets/image/'+item.img+'.svg')" alt="">
                <span class="bg__media"></span>
            </div>
            <div class="t-tab__text">
                <h2 class="t-tab__text__title">{{ item.title }}</h2>
                <p class="t-tab__text__p">{{ item.description }}</p>
                <div class="t-tab__text__buttons">
                <button class="btn btn__blue__plain btn__center">{{ item.button }}</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TabsItems',
      props: {
        file: {
            type: Array,
            default() {
                return {}
            }
        }
    }    
}
</script>

