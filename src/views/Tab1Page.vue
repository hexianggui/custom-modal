<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Tab 1</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Tab 1</ion-title>
        </ion-toolbar>
      </ion-header>
      <ion-button @click="setModalOpen(true)">Open the first modal</ion-button>
      <ion-modal :is-open="isOpenModal">
        <ion-header >
          <ion-toolbar color="primary">
            <ion-title>FirstModal</ion-title>
            <ion-buttons slot="end">
              <ion-button @click="setModalOpen(false)">CLOSE</ion-button>
            </ion-buttons>
          </ion-toolbar>
        </ion-header>
        <first-modal></first-modal>
      </ion-modal>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
  IonModal,
  IonButton,
  IonButtons,
} from "@ionic/vue";
import FirstModal from "@/components/first-modal.vue";

export default defineComponent({
  name: "Tab1Page",
  components: {
    IonButton,
    IonModal,
    FirstModal,
    IonHeader,
    IonToolbar,
    IonTitle,
    IonContent,
    IonPage,
    IonButtons,
  },
  setup() {
    const isOpenModal = ref(false);
    const setModalOpen = (b: boolean) => {
      isOpenModal.value = b;
    };
    return { isOpenModal, setModalOpen };
  },
});
</script>
