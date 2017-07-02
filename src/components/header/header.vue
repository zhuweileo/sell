<template>
    <div class="header">
        <div class="content-wrapper">
            <div class="avatar">
                <img :src="seller.avatar" alt="">
            </div>
            <div class="content">
                <div class="title">
                    <span class="brand"></span>
                    <span class="name">{{seller.name}}</spa>
                </div>
                <div class="distribution">
                    {{seller.description}}/{{seller.deliveryTime}}分钟送达
                </div>
                <div class="activity" v-if="seller.supports">
                    <span class="icon"></span>
                    <span class="description">{{seller.supports[0].description}}</span>
                </div>
            </div>
        </div>
    </div>
</template>

<script type="text/ecmascript-6">
export default {
    props: {
        seller: {
            type: Object
        }
    }
};
</script>

<style lang="scss">
@import "../../../common/scss/mixin.scss";
.header {
    color: #fff;
    background: #000;
    .content-wrapper {
        font-size: 0;
        .avatar {
            padding: 24px 16px 18px 24px;
            display: inline-block;
            img {
                width: 64px;
                height: 64px; // vertical-align: top;
            }
        }
        .content {
            display: inline-block;
            .title {
                font-size: 16px;
                .brand {
                    @include bg-img('brand');
                    width: 30px;
                    height: 18px;
                    display:inline-block;
                    background-size: 30px 18px;
                    vertical-align: top;
                }
            }
            .distribution {
                font-size: 12px;
            }
            .activity {
                font-size: 12px;
            }
        }
    }
}
</style>
