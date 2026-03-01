<template>
  <div class="common-container">
    <section>
      <el-descriptions
        v-for="item of repairSitesList"
        :column="2"
        direction="vertical"
        :title="item.city"
        border
      >
        <el-descriptions-item>
          <template #label>
            <div class="cell-item">
              <el-icon>
                <user />
              </el-icon>
              {{ $t('repair.contact') }}
            </div>
          </template>
          {{ item.contact }}
        </el-descriptions-item>
        <el-descriptions-item>
          <template #label>
            <div class="cell-item">
              <el-icon>
                <iphone />
              </el-icon>
              {{ $t('repair.telephone') }}
            </div>
          </template>
          {{ item.telephone }}
        </el-descriptions-item>
        <el-descriptions-item>
          <template #label>
            <div class="cell-item">
              <el-icon>
                <office-building />
              </el-icon>
              {{ $t('repair.address') }}
            </div>
          </template>
          {{ item.address }}
        </el-descriptions-item>
      </el-descriptions>
    </section>
  </div>
</template>

<script lang="ts" setup>
import { ElIcon, ElDescriptions, ElDescriptionsItem } from 'element-plus'

const locale = useCookie('locale')
const repairSitesList = computed(() => {
  switch (locale.value) {
    case 'cn':
      return repairSitesListCN
    case 'ru':
      return repairSitesListRU
    default:
      return repairSitesListEN
  }
})
const repairSitesListCN = [
  {
    city: '美国德克萨斯',
    contact: '王赠涵',
    address: '德克萨斯州布鲁克希尔市金斯兰大道30625号428单元',
    telephone: '(432)924-7069',
  },
  {
    city: '中国. 深圳',
    contact: '唐乾高',
    address: '深圳市宝安区石岩街道伟泰工业园1号厂房404',
    telephone: ' +86 176 8876 7856',
  },
]

const repairSitesListEN = [
  {
    city: 'Texas,USA',
    contact: 'Zenghan Wang',
    address: '30625 Kingsland Blvd, unit 428, Brookshire, TX 77423',
    telephone: '(432)924-7069',
  },
  {
    city: 'Shenzhen,China',
    contact: 'Tang Qiangao ',
    address: 'Room 404, Building 1, Weitai Industrial Park, Shiyan Street, Baoan District, Shenzhen',
    telephone: '+86 176 8876 7856',
  },

]

const repairSitesListRU = [
  {
    city: 'Техас, США',
    contact: 'Zenghan Wang',
    address: '30625 Kingsland Blvd, квартира 428, Брукшир, Техас 77423',
    telephone: ' (432)924-7069',
  },
  {
    city: 'Shenzhen,China',
    contact: 'Tang Qiangao ',
    address: 'Комната 404, заводское здание № 1, промышленный парк Вэйтай, улица Шиянь, район Баоань, город Шэньчжэнь',
    telephone: '+86 176 8876 7856',
  },
  
]
</script>

<style lang="less" scoped>
section {
  width: 1080px;
  margin: 0 auto 50px;
  padding-top: 50px;
}

.el-descriptions {
  margin-top: 20px;
}

.cell-item {
  display: flex;
  align-items: center;
}

.el-icon {
  margin-bottom: 2px;
}

@media (max-width: 1024px) {
  section {
    width: 100%;
  }
}
</style>
