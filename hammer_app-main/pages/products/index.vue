<template>
  <div class="common-container">
    <section class="banner">
      <div class="content d-flex-between">
      </div>
    </section>
    <section class="wide-section">
      <div class="content detail-only wide-detail">
        <img class="detail-image" :src="detail1Image" alt="detail-1">
      </div>
    </section>
    <section class="wide-section">
      <div class="title">{{ $t('products.modes') }}</div>
      <div class="content detail-only wide-detail">
        <img class="detail-image" :src="detail2Image" alt="detail-2">
      </div>
    </section>
    <section class="wide-section">
      <div class="title">{{ $t('products.roi') }}</div>
      <div class="content detail-only wide-detail">
        <img class="detail-image" :src="detail3Image" alt="detail-3">
      </div>
    </section>
    <section class="wide-section">
      <div class="title">{{ $t('products.service') }}</div>
      <div class="content detail-only wide-detail">
        <img class="detail-image" :src="detail4Image" alt="detail-4">
      </div>
    </section>
  </div>
</template>

<script lang="ts" setup>
const locale = useCookie<string>('locale')

const detail1Image = computed(() => {
  const lang = locale.value || 'en'
  return `/img/products/${lang}/detail-1.jpg`
})

const detail2Image = computed(() => {
  const lang = locale.value || 'en'
  return `/img/products/${lang}/detail-2.jpg`
})

const detail3Image = computed(() => {
  const lang = locale.value || 'en'
  return `/img/products/${lang}/detail-3.jpg`
})

const detail4Image = computed(() => {
  const lang = locale.value || 'en'
  return `/img/products/${lang}/detail-4.jpg`
})
</script>

<style lang="less" scoped>
section {
  width: 1080px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  margin: 0 auto 20px;
  font-weight: bold;

  &.wide-section {
    width: 1650px;
    max-width: calc(100vw - 40px);
  }

  .title {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 500px;
    height: 40px;
    margin-bottom: 0;
    text-align: center;
    color: #fff;
    font-size: 26px;

    &.no-margin {
      margin-bottom: 10px;
    }
  }

  .sub-title {
    font-size: 26px;
    color: @main-color;
    margin-bottom: 10px;
  }

  .content {
    width: 100%;
    height: 400px;

    &.detail-only {
      width: 100%;
      height: auto;

      .detail-image {
        width: 100%;
        display: block;
      }
    }

    &.wide-detail {
      width: 1650px;
      max-width: 100%;
    }

    .miner-box {
      width: 60%;
      height: 100%;
      background-color: rgb(244, 244, 244);
      box-shadow: -12px 12px 0px @main-color;

      img {
        width: 80%;
      }
    }

    .data-box {
      width: 40%;
      height: 100%;
      border: 2px solid @main-color;
      border-left: none;

      .power {
        display: block;
        width: 80%;
        margin: 0 auto;
        font-size: 24px;
      }
    }

    &.reverse {
      flex-direction: row-reverse;

      .miner-box {
        box-shadow: 12px 12px 0px @main-color;
      }

      .data-box {
        border-left: 2px solid @main-color;
        border-right: none;
      }
    }

    .mode-box {
      width: 100%;
      height: 80%;
      position: relative;

      .mode-cycle {
        display: flex;
        justify-content: center;
        align-items: center;
        text-align: center;
        width: 180px;
        height: 180px;

        &.low {
          position: absolute;
          top: 10px;
          left: 10px;
          background: url('/img/low-mode.png');
          background-position: center;
          background-size: cover;
        }

        &.high {
          position: absolute;
          right: 10px;
          bottom: 10px;
          background: url('/img/high-mode.png');
          background-position: center;
          background-size: cover;
        }
      }
    }

    .warn {
      color: red;
      text-align: center;
      margin: 10px 5px 0;
    }

    .payback-box {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;

      div {
        font-size: 20px;
      }

      span {
        font-size: 36px;
        color: @main-color;
      }

      img {
        width: 70%;
        margin: 20px 0;
      }
    }
  }

  .address {
    width: 100%;
    position: relative;

    img {
      width: 100%;
    }
  }

  .tips {
    width: 100%;
    box-sizing: border-box;
    position: absolute;
    bottom: 0;
    padding: 10px;
    background: rgba(#fff, 0.3)
  }
}

.banner {
  width: 100vw;
  height: 36vw;
  margin-bottom: 60px;
  color: #fff;
  background: url('/img/banner-2.jpg');
  background-size: cover;

  .content {
    height: 100%;
    padding: 20px;
    box-sizing: border-box;

  }
}

@media (max-width: 1024px) {
  .common-container {
    margin: 60px 0;
  }

  section {
    width: 100%;
    padding: 0 20px;
    box-sizing: border-box;
    font-size: 12px;

    .title {
      width: 300px;
      font-size: 20px;
    }

    .sub-title {
      font-size: 20px;
    }

    .content {
      height: 300px;

      &.detail-only {
        height: auto;
      }

      .miner-box {
        width: 50%;
        box-shadow: -5px 5px 0px @main-color;
      }

      &.reverse {
        .miner-box {
          box-shadow: 5px 5px 0px @main-color;
        }
      }

      .data-box {
        width: 50%;
      }

      .mode-box {
        height: 78%;

        .mode-cycle {
          width: 110px;
          height: 110px;
        }
      }

      .warn {
        margin: 0px 2px;
      }

      .payback-box {
        div {
          text-align: center;
          font-size: 13px;
        }

        span {
          font-size: 16px;
        }

        img {
          width: 80%;
        }
      }
    }

    .tips {
      width: 100%;
    }
  }
}</style>
