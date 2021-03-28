<template>
    <div class="contain__links">

        <div class="n-tabs">
            <ul class="n-tabs__list">
                <li 
                v-for="(link, index) in file"
                :key="link.idLink"
                @click="emitGoTab(link.idLink)"
                :data-id="link.idLink"
                :class="[index == 0 ? 'active' : '']"
                class="n-tabs__link">
                    <span>{{ link.link }}</span>
                </li>
            </ul>
        </div>

    </div>
</template>

<script>
export default {
    name: 'TabsLinks',
    props: {
        file: {
            type: Array,
            default() {
                return []
            }
        }
    },
    methods: {
        emitGoTab(id) {
        this.$emit("emit-go-tab", { message: id});
        },
    }
}
</script>


