<template>
  <div class="common-container">
    <section>
      <h1 class="title">{{ $t('firmware.title') }}</h1>
      <div class="button-bar d-flex">
        <a
          href=""
          class="d-flex-center"
          >{{ $t('firmware.upgrade') }}</a
        >
        <a
          href=""
          class="d-flex-center"
          >{{ $t('firmware.card') }}</a
        >
        <a
          :href="locale === 'en' ?"
          class="d-flex-center"
          >{{ $t('firmware.guide') }}</a
        >
      </div>

      <el-table
        :data="tableData"
        border
        style="width: 100%"
      >
        <el-table-column
          prop="name"
          :label="$t('firmware.name')"
          width="200"
        >
        </el-table-column>
        <el-table-column
          prop="size"
          :label="$t('firmware.file')"
          width="160"
        >
        </el-table-column>
        <el-table-column
          prop="description"
          :label="$t('firmware.description')"
        >
        </el-table-column>
        <el-table-column
          prop="time"
          :label="$t('firmware.date')"
          width="200"
        >
        </el-table-column>
        <el-table-column
          :label="$t('firmware.action')"
          width="100"
          align="center"
        >
          <template #default="scope">
            <el-button
              class="action-button"
              @click="download(scope.row.link)"
            >
              <el-icon>
                <Download />
              </el-icon>
            </el-button>
            <el-button
              class="action-button"
              @click="share(scope.row.link)"
            >
              <el-icon>
                <Share />
              </el-icon>
            </el-button>
          </template>
        </el-table-column>
      </el-table>
    </section>
  </div>
</template>

<script lang="ts" setup>
import { useI18n } from 'vue-i18n'
import { ElIcon, ElButton, ElTable, ElTableColumn, ElMessage } from 'element-plus'

const locale = useCookie('locale')

const i18n = useI18n()

const tableData = [
  {
    name: i18n.t(' '),
    description: i18n.t(' '),
    size: ' ',
    time: ' ',
    link: ' ',
  },
]

const download = (link: string) => {
  const a = document.createElement('a')
  a.href = link
  a.click()
}

const share = async (link: string) => {
  try {
    navigator.clipboard.writeText(window.location.host + link)
    ElMessage({
      message: i18n.t('common.share'),
      type: 'success',
      offset: 200,
      center: true,
    })
  } catch (e) {
    console.log(e)
  }
}
</script>

<style lang="less" scoped>
section {
  width: 1080px;
  margin: 0 auto 50px;
  padding-top: 50px;

  .title {
    width: fit-content;
    font-size: 24px;
    margin-bottom: 40px;
  }

  .button-bar {
    margin-bottom: 40px;

    a {
      width: 150px;
      height: 40px;
      margin-right: 20px;
      text-align: center;
      color: #fff;
      border-radius: 4px;
      background-color: @main-color;

      &:hover {
        background-color: fade(@main-color, 80%);
      }
    }
  }
}

.action-button {
  width: 50px;
  height: 25px;
  margin: 2px auto;
}

@media (max-width: 1024px) {
  section {
    width: 100%;
  }
}
</style>
