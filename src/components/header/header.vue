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
        <div class="supports" v-if="seller.supports">
          <span class="icon" :class="iconMap[seller.supports[0].type]"></span>
          <span class="description">{{seller.supports[0].description}}</span>
        </div>
        <div class="supports-count" v-if="seller.supports" @click="showDe">
          <span class="count">{{seller.supports.length}}个</span>
          <i class="icon-keyboard_arrow_right"></i>
        </div>
      </div>
    </div>
    <div class="bulletin-wrapper">
      <span class="bulletin-title"></span><span class="bulletin-text">{{seller.bulletin}}</span><i
      class="icon-keyboard_arrow_right"></i>
    </div>
    <div class="background">
      <img :src="seller.avatar" alt="">
    </div>
    <div class="detial" v-show="showDetail">
      <div class="detial-content">
        <h1 class="name">{{seller.name}}</h1>
        <div class="star-wrapper">
          <star :size="48" :score="seller.score"></star>
        </div>
        <div class="favor">
          <div class="title">
            <div class="line"></div>
            <div class="text">优惠信息</div>
            <div class="line"></div>
          </div>
        </div>
        <div class="notice">
          <p class="bulletin">{{seller.bulletin}}</p>
        </div>
      </div>
      <div class="detial-footer"><span class="icon-close"></span></div>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
  import star from '../star/star.vue';
  export default {
    props: {
      seller: {
        type: Object
      }
    },
    data() {
      return {
        showDetail: false,
        iconMap: ['decrease', 'discount', 'special', 'invoice', 'guarantee']
      };
    },
    methods: {
      showDe() {
        this.showDetail = !this.showDetail;
      }
    },
    created() {
//        this.iconMap = ['descrease', 'discount', 'special', 'invoice', 'guarantee'];
    },
    components: {
      star
    }
  };
</script>

<style lang="scss">
  @import "../../../common/scss/mixin.scss";

  .header {
    color: #fff;
    position: relative;
    background: rgba(7, 17, 27, .5);
    overflow: hidden;
    .content-wrapper {
      font-size: 0;
      padding: 24px 16px 18px 24px;
      position: relative;
      .avatar {
        margin-right: 16px;
        display: inline-block;
        img {
          width: 64px;
          height: 64px; // vertical-align: top;
          border-radius: 2px;
        }
      }
      .content {
        display: inline-block;
        vertical-align: top;
        .title {
          font-size: 0;
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
        .supports {
          font-size: 10px;
          margin-top: 10px;
          .icon {
            display: inline-block;
            margin-right: 4px;
            vertical-align: middle;
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
          .description {
            line-height: 12px;
            vertical-align: baseline;
            font-size: 10px; //手机可以显示10px
          }
        }
        .supports-count {
          position: absolute;
          right: 12px;
          bottom: 12px;
          background: rgba(255, 255, 255, .2);
          border-radius: 12px;
          padding: 0 8px;
          .count {
            margin-right: 2px;
            line-height: 24px;
            height: 24px;
            font-size: 10px;
            /*vertical-align: middle;*/
          }
          .icon-keyboard_arrow_right {
            line-height: 24px;
            font-size: 10px;
            /*color: white;*/
            vertical-align: -1px;
          }
        }
      }
    }
    .bulletin-wrapper {
      height: 28px;
      line-height: 28px;
      padding: 0 22px 0 12px;
      background: rgba(7, 17, 27, .2);
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
      position: relative;
      .bulletin-title {
        margin-right: 4px;
        display: inline-block;
        width: 22px;
        height: 12px;
        background-size: 22px 12px;
        background-repeat: no-repeat;
        @include bg-img("bulletin");
      }
      .bulletin-text {
        font-size: 10px;
        vertical-align: top;
      }
      .icon-keyboard_arrow_right {
        position: absolute;
        right: 12px;
        line-height: 28px;
        font-size: 10px;
      }

    }
    .background {
      img {
        position: absolute;
        top: 0;
        left: 0;
        z-index: -1;
        width: 100%;
        height: 100%;
        filter: blur(10px);
      }
    }
    .detial {
      overflow: auto;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100vh;
      background: rgba(7, 17, 27, .8);
      z-index: 1;
      /*filter:blur(10px);*/
      display: flex;
      flex-direction: column;
      /*overflow:auto;*/
      .detial-content {
        flex-grow: 1;
        padding-top: 64px;
        padding-left:36px;
        padding-right:36px;
        .name {
          text-align: center;
          font-size: 16px;
          line-height: 16px;
          font-weight: 700;
          color: #fff;
        }
        .star-wrapper{
          text-align:center;
          padding-top:16px;
          padding-bottom:28px;
        }
        .favor{
          .title{
            display:flex;
            .line{
              border-top:1px solid rgba(255,255,255,.2);
              flex-grow:1;
              position:relative;
              top:7px;
            }
            .text{
              font-size:14px;
              line-height:14px;
              font-weight:700;
              padding:0 12px;
            }
          }
        }
      }
      .detial-footer {
        text-align: center;
        padding-top: 32px;
        padding-bottom: 32px;
        .icon-close {
          color: rgba(255, 255, 255, .5);
          font-size: 32px;
        }
      }
    }
  }
</style>
