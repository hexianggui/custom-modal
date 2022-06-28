<template>
  <ion-page>
    <ion-content :fullscreen="true">
      <h1>This is the underlying Modal</h1>
      <div >
        <p>Error, open IconModal repeatedly</p>
        <ion-button @click="setModalOpen(true)"
          >Open Modal load Amap</ion-button
        >
      </div>
      <div >
        <p>How do I get focus custom Modal turned on in Modal </p>
        <ion-button @click="setModalCustomOpen(true)"
          >Open the custom Modal</ion-button
        >
      </div>
    </ion-content>
    <ion-modal :is-open="isOpenModal">
      <ion-toolbar color="primary">
        <ion-title>Custom Modal</ion-title>
        <ion-buttons slot="end">
          <ion-button @click="isOpenModal = false">CLOSE</ion-button>
        </ion-buttons>
      </ion-toolbar>
      <ion-content :fullscreen="true">
        <amap-test></amap-test>
      </ion-content>
    </ion-modal>
    <teleport to="body">
      <div
        v-if="isOpenCustomModal"
        style="
          width: 100%;
          height: 100%;
          z-index: 99999999;
          position: absolute;
          top: 0px;
          left: 0px;
          background-color: white;
        "
      >
        <ion-toolbar color="primary">
          <ion-title>Custom Modal</ion-title>
          <ion-buttons slot="end">
            <ion-button @click="isOpenCustomModal = false">CLOSE</ion-button>
          </ion-buttons>
        </ion-toolbar>
        <div>
          <div style="text-align: center"><h2>Unable to get focus</h2></div>

          <ion-item>
            <ion-label>FetFocus</ion-label>
            <ion-input placeholder="Unable to get focus"></ion-input>
          </ion-item>
           <amap-test></amap-test>
        </div>
      </div>
    </teleport>
  </ion-page>
</template>

<script lang="ts">
import {
  IonButton,
  IonContent,
  IonToolbar,
  IonPage,
  IonTitle,
  IonButtons,
  IonLabel,
  IonInput,
  IonItem,
  IonModal,
} from "@ionic/vue";
import { defineComponent, ref } from "vue";
import AmapTest from "@/components/amap-test.vue";
export default defineComponent({
  components: {
    IonButton,
    IonContent,
    IonToolbar,
    IonPage,
    IonTitle,
    IonButtons,
    IonLabel,
    IonInput,
    IonItem,
    AmapTest,
    IonModal,
  },
  props: {},
  setup() {
    const isOpenModal = ref(false);
    const setModalOpen = (b: boolean) => {
      console.log(123);
      isOpenModal.value = b;
    };
    const isOpenCustomModal = ref(false);
    const setModalCustomOpen = (b: boolean) => {
      console.log(123);
      isOpenCustomModal.value = b;
    };
    return { isOpenModal, setModalOpen, isOpenCustomModal, setModalCustomOpen };
  },
});
</script>

<style scoped></style>
