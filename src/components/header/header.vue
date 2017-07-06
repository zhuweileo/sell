<template>
  <div class="header">
    <div class="content-wrapper">
      <div class="avatar">
        <img :src="seller.avatar" alt="">
      </div>
      <div class="content">
        <div class="title">
          <span class="brand"></span>
          <span class="name">{{seller.name}}</span>
        </div>
        <div class="distribution">
          {{seller.description}}/{{seller.deliveryTime}}分钟送达
        </div>
        <div class="activity" v-if="seller.supports">
          <span class="icon" :class="iconMap[seller.supports[0].type]"></span>
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
    },
    data() {
      return {
        iconMap: ['decrease', 'discount', 'special', 'invoice', 'guarantee']
      };
    },
    created() {
//        this.iconMap = ['descrease', 'discount', 'special', 'invoice', 'guarantee'];
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
      padding: 24px 16px 18px 24px;
      .avatar {
        margin-right: 16px;
        display: inline-block;
        img {
          width: 64px;
          height: 64px; // vertical-align: top;
          border-radius:2px;
        }
      }
      .content {
        display: inline-block;
        vertical-align: top;
        .title {
          font-size: 0px;
          margin-top: 2px;
          .brand {
            @include bg-img('brand');
            width: 30px;
            height: 18px;
            display: inline-block;
            background-size: 30px 18px;
            vertical-align: top;
            margin-right: 6px;
          }
          .name {
            font-size: 16px;
            font-weight: bold;
            line-height: 18px;
          }
        }
        .distribution {
          font-size: 12px;
          margin-top: 8px;
        }
        .activity {
          font-size: 0;
          margin-top: 10px;
          .icon {
            display: inline-block;
            margin-right:4px;
            vertical-align:top;
            width: 12px;
            height: 12px;
            background-size: 12px 12px;
            background-repeat: no-repeat;
            &.decrease {
              @include bg-img('decrease_1');
            }
            &.discount {
              @include bg-img('discount_1');
            }
            &.guarantee {
              @include bg-img('guarantee_1');
            }
            &.invoice {
              @include bg-img('invoice_1');
            }
            &.special {
              @include bg-img('special_1');
            }
          }
          .description{
            line-height:12px;
            font-size:10px;//手机可以显示10px
          }
        }
      }
    }
  }
</style>
