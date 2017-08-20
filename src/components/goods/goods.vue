<template>
    <div class="goods">
        <div class="menu-wrapper">
            <ul>
                <li v-for="item in goods">

                </li>
            </ul>
        </div>
        <div class="foods-wrapper"></div>
    </div>
</template>
<script type="text/ecmascript-6">
const OK = 0;
export default {
    props: {
        seller: Object
    },
    data() {
        return {
            goods: []
        };
    },
    created() {
        this.$http.get('/api/goods').then((response) => {
            response = response.body;
            if (response.errno === OK) {
                this.goods = response.data;
            };
        });
    }
};
</script>

<style lang="scss">
.goods {
    display: flex;
    position: absolute;
    top: 174px;
    bottom: 46px;
    width: 100%;
    .menu-wrapper {
        flex: 0 0 80px;
        background: #f3f5f7;
        width: 80px;
    }
    .foods-wrapper {
        flex: 1;
    }
}
</style>