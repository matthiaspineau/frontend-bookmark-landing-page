<template>
    <div class="container contain__tabs">
        <slot name="link"></slot>
        <slot name="tab"></slot>
    </div>
</template>

<script>
export default {
    name: 'TabsContainer'
}
</script>

<style lang="scss" scoped>
.contain__tabs {
    margin-top: 35px;
}
</style>