<template>
  <el-container style="max-height: 100vh">
    <el-header>
      <AppHeader />
    </el-header>
    <el-container>
      <el-aside>
        <IncidentList />
      </el-aside>
      <el-main style="display: flex; flex-direction: column; padding: 0px">
        <CallControls />
        <div style="display: flex; flex: 1">
          <AppChat style="width: 70%" v-if="incidentStore.selectedIncident" />
          <IncidentInfo style="width: 30%" v-if="incidentStore.selectedIncident" />
          <p class="main__empty-label" v-else>Выберите обращение чтобы начать работу</p>
        </div>
      </el-main>
    </el-container>
  </el-container>
  <ModalsContainer />
  <IncomingCallModal />
</template>

<script lang="ts" setup>
import { useIncidentStore } from '@/stores/incidentStore';
import IncomingCallModal from '@/components/IncomingCallModal.vue';
import AppHeader from '@/layouts/AppHeader.vue';
import CallControls from '@/components/CallControls.vue';

const incidentStore = useIncidentStore();
</script>

<style lang="scss" scoped>
.main {
  &__empty-label {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
    width: 100%;
  }
}
</style>
