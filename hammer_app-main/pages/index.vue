<template>
  <div class="common-container">
    <swiper
      :active-index="activeIndex"
      :modules="modules"
      :slides-per-view="1"
      :space-between="50"
      :autoplay="{ delay: 5000 }"
      :pagination="{ clickable: true }"
      @slideChange="slideChange"
    >


      <swiper-slide>
        <section
          class="banner"
          id="banner00"
        >
        </section>
      </swiper-slide>

          <swiper-slide>
        <section
          class="banner"
          id="banner11"
        >
        </section>
      </swiper-slide>
      
      
       <swiper-slide>
        <section
          class="banner"
          id="banner22"
        >
        </section>
      </swiper-slide>
      
   
       <swiper-slide>
        <section
          class="banner"
          id="banner33"
        >
        </section>
      </swiper-slide>
      
      <swiper-slide>
        <section
          class="banner"
          id="banner44"
        >
        </section>
      </swiper-slide>


      <swiper-slide>
        <section
          class="banner"
          id="banner55"
        >
        </section>
      </swiper-slide>

  

      
      
    
    </swiper>
    <section class="params-seciton">
      <div class="title">
        <div>{{ $t('home.params') }}</div>
        <img src="/img/sub-line.png" />
      </div>
      <div class="content d-flex">
        <div
          v-for="item of paramsList"
          class="params-box"
        >
          <img
            class="describe mb10"
            :src="`/img/params${item.id}.png`"
          />
          <div
            class="describe-title"
            v-html="$t(`home.product${activeIndex}.params${item.id}_title`)"
          />
          <div class="params">
            <div v-for="params of item.paramsNum">
              {{ $t(`home.product${activeIndex}.params${item.id}_${params}`) }}
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="shop-section">
      <div class="title">
        <div>{{ $t('home.shop') }}</div>
        <img src="/img/sub-line.png" />
      </div>
      <div class="content d-flex-between">
        <a
          v-for="item of shopsList"
          :href="item.link"
          target="_blank"
        >
          <img
            :src="item.image || `/img/${item.name}.png`"
          />
        </a>
      </div>
    </section>
  </div>
</template>

<script lang="ts" setup>
import { Pagination, A11y, Autoplay } from 'swiper'

// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from 'swiper/vue'
// Import Swiper styles
import 'swiper/css'
import 'swiper/css/autoplay'
import 'swiper/css/pagination'

const modules = [Pagination, A11y, Autoplay]

const activeIndex = ref(0)
const slideChange = (swiper: any) => {
  activeIndex.value = swiper.activeIndex
}

const paramsList = computed(() => {
  switch (activeIndex.value) {
    case 0:
      return [
        {
          id: '01',
          paramsNum: 1,
        },
        {
          id: '02',
          paramsNum: 1,
        },
        {
          id: '03',
          paramsNum: 1,
        },
           {
          id: '04',
          paramsNum: 1,
        },
      ]
    case 1:
      return [
        {
          id: '01',
          paramsNum: 3,
        },
        {
          id: '02',
          paramsNum: 5,
        },
        {
          id: '03',
          paramsNum: 4,
        },
        {
          id: '04',
          paramsNum: 7,
        },
      ]
    case 2:
      return [
        {
          id: '01',
          paramsNum: 3,
        },
        {
          id: '02',
          paramsNum: 5,
        },
        {
          id: '03',
          paramsNum: 4,
        },
        {
          id: '04',
          paramsNum: 7,
        },
      ]     
        case 3:
      return [
        {
          id: '01',
          paramsNum: 3,
        },
        {
          id: '02',
          paramsNum: 5,
        },
        {
          id: '03',
          paramsNum: 4,
        },
        {
          id: '04',
          paramsNum: 7,
        },
      ]    
        case 4:
      return [
        {
          id: '01',
          paramsNum: 3,
        },
        {
          id: '02',
          paramsNum: 5,
        },
        {
          id: '03',
          paramsNum: 4,
        },
        {
          id: '04',
          paramsNum: 7,
        },
      ]    
             case 5:
      return [
        {
          id: '01',
          paramsNum: 1,
        },
        {
          id: '02',
          paramsNum: 1,
        },
        {
          id: '03',
          paramsNum: 1,
        },
        {
          id: '04',
          paramsNum: 1,
        },
      ]   
             case 6:
      return [
        {
          id: '01',
          paramsNum: 1,
        },
        {
          id: '02',
          paramsNum: 1,
        },
        {
          id: '03',
          paramsNum: 1,
        },
        {
          id: '04',
          paramsNum: 1,
        },
      ]   
    default:
      return [
        {
          id: '01',
          paramsNum: 3,
        },
        {
          id: '02',
          paramsNum: 4,
        },
        {
          id: '03',
          paramsNum: 4,
        },
        {
          id: '04',
          paramsNum: 7,
        },
      ]
  }
})

const shopsList = ref([
  {
    name: 'amazon',
    link: '//www.amazon.com/dp/B0BHNQ3GM6',
  },
  {
    name: 'ebay',
    link: '//www.ebay.com/itm/354136904551',
  },
  {
    name: 'plebSource',
    link: '//plebsource.com/',
    image: '/img/plebSource.png',
  },
])

</script>

<style lang="less" scoped>
section {
  width: 1080px;
  margin: 0 auto 50px;

  .title {
    width: fit-content;
    font-size: 24px;
    margin-bottom: 40px;

    img {
      width: 100%;
      max-width: 300px;
      height: 8px;
    }
  }
}

.banner {
  width: 100vw;
  height: 36vw;
  color: #fff;
  
 &#banner00 {
    background: #1b1b1b url('/img/banner00.jpg');
    background-size: cover;
  }

        &#banner11 {
    background: #1b1b1b url('/img/banner11.jpg');
    background-size: cover;
  }
  
   &#banner22 {
    background: #1b1b1b url('/img/banner22.jpg');
    background-size: cover;
  }
    

  &#banner33{
    background: #1b1b1b url('/img/banner33.jpg');
    background-size: cover;
  }
    &#banner44 {
    background: #1b1b1b url('/img/banner44.jpg');
    background-size: cover;
  }

  
    &#banner55 {
    background: #1b1b1b url('/img/banner55.jpg');
    background-size: cover;
  }




  .miner {
    width: 20vw;
  }

  .num {
    font-family: 'Roboto';
  }

  h2 {
    font-size: 4vw;
    font-weight: normal;
  }

  h3 {
    font-size: 2vw;
    font-weight: normal;
  }
}

.params-seciton {
  .content {
    flex-wrap: wrap;
    border: 1px solid @main-color;

    .params-box {
      flex: 1;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 20px;

      .title {
        margin-bottom: 10px;
      }

      .describe {
        width: 25%;
      }

      .describe-title {
        font-size: 20px;
        margin-bottom: 10px;
        text-align: center;
        color: rgba(83, 86, 87);
        font-weight: bold;
      }

      &:nth-child(even) {
        background-color: @main-color;
        color: #fff;

        .describe-title {
          color: #fff;
        }
      }

      .params {
        width: 100%;
        text-align: left;
      }
    }
  }
}

.shop-section {
  .content {
    width: 60%;
    margin: 0 auto;
    gap: 20px;
    align-items: center;

    img {
      max-height: 100px;
      max-width: 100%;
      height: auto;
      width: auto;
      object-fit: contain;
    }
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

    .title {
      font-size: 18x;
    }
  }

  .banner {
    &#banner02 {
      .content {
        width: 80%;

        .split-line {
          width: 120px;
          margin: 10px 0;
        }

        span {
          font-size: 12px;
        }
      }
    }
  }

  .params-seciton {
    .content {
      .params-box {
        box-sizing: border-box;
        flex: auto;
        width: 100%;
      }
    }
  }

  .shop-section {
    .content {
      width: 100%;
      margin: 0 auto;
    }
  }
}
</style>
