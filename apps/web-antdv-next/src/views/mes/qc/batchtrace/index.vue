<script lang="ts" setup>
import type { VxeTableGridOptions } from '#/adapter/vxe-table';
import type { MesWmBatchApi } from '#/api/mes/wm/batch';

import { DocAlert, Page, useVbenModal } from '@vben/common-ui';

import { ACTION_ICON, TableAction, useVbenVxeGrid } from '#/adapter/vxe-table';
import { getBatchPage } from '#/api/mes/wm/batch';

import { useGridColumns, useGridFormSchema } from './data';
import TraceDetail from './modules/trace-detail.vue';

const [DetailModal, detailModalApi] = useVbenModal({
  connectedComponent: TraceDetail,
  destroyOnClose: true,
});

/** 打开批次追溯详情 */
function handleTrace(row: MesWmBatchApi.Batch) {
  detailModalApi.setData(row).open();
}

const [Grid] = useVbenVxeGrid({
  formOptions: {
    schema: useGridFormSchema(),
  },
  gridOptions: {
    columns: useGridColumns(),
    height: 'auto',
    keepSource: true,
    proxyConfig: {
      ajax: {
        query: async ({ page }, formValues) => {
          return await getBatchPage({
            pageNo: page.currentPage,
            pageSize: page.pageSize,
            ...formValues,
          });
        },
      },
    },
    rowConfig: {
      keyField: 'id',
      isHover: true,
    },
    toolbarConfig: {
      refresh: true,
      search: true,
    },
  } as VxeTableGridOptions<MesWmBatchApi.Batch>,
});
</script>

<template>
  <Page auto-content-height>

    <DetailModal />

    <Grid table-title="批次追溯列表">
      <template #actions="{ row }">
        <TableAction
          :actions="[
            {
              label: '批次追溯',
              type: 'link',
              icon: ACTION_ICON.VIEW,
              auth: ['mes:wm-batch:query'],
              onClick: handleTrace.bind(null, row),
            },
          ]"
        />
      </template>
    </Grid>
  </Page>
</template>
