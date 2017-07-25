<template>
  <div class="star" :class="starType">
    <span class="star-item" v-for="itemClass in itemClasses" :class="itemClass" track-by="$index"></span>
  </div>
</template>

<script>
  const STAR_ON = 'on';
  const STAR_OFF = 'off';
  const STAR_HALF = 'half';
  export default {
    props: {
      size: {
        type: Number
      },
      score: {
        type: Number
      }
    },
    computed: {
      starType() {
        return 'star-' + this.size;
      },
      itemClasses() {
        let stars = [];
        // 将score精确到0.5
        let num = Math.floor(this.score * 2) / 2;
        let hasHalf = num % 1 !== 0;
        for (let i = 0; i < parseInt(num); i++) {
            stars.push(STAR_ON);
        }
        if (hasHalf) stars.push(STAR_HALF);
        let len = stars.length;
        if (len > 5) return stars.slice(0, 5);
        for (let j = 0; j < 5 - len; j++) {
            stars.push(STAR_OFF);
        }
        return stars;
      }
    }
  };
</script>

<style lang="scss">
  @import "../../../common/scss/mixin";
  .star{
    display: inline-block;
    /*font-size:0;*/
    .star-item{
      display:inline-block;
    }
    &.star-24{
      .star-item{
        width:10px;
        height:10px;
        margin-right:3px;
        background-size:10px 10px;
        &:last-child{
          margin-right:0;
        }
      }
      .on{
        @include bg-img('./img/star24_on')
      }
      .off{
        @include bg-img('./img/star24_off')
      }
      .half{
        @include bg-img('./img/star24_half')
      }
    }
    &.star-36{
      .star-item{
        margin-right:6px;
        width:15px;
        height:15px;
        background-size: 15px 15px;
        &:last-child{
          margin-right:0;
        }
      }
      .on{
        @include bg-img('./img/star36_on')
      }
      .off{
        @include bg-img('./img/star36_off')
      }
      .half{
        @include bg-img('./img/star36_half')
      }
    }
    &.star-48{
      .star-item{
        margin-right:22px;
        width:20px;
        height:19px;
        background-size:20px 19px;
        &:last-child{
          margin-right:0;
        }
      }
      .on{
        @include bg-img('./img/star48_on')
      }
      .off{
        @include bg-img('./img/star48_off')
      }
      .half{
        @include bg-img('./img/star48_half')
      }
    }
  }
</style>
