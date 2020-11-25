<template>
  <q-page>
    <div class="flex flex-center">
      <q-tabs v-model="tab" class="text-teal q-mx-sm full-width">
        <q-tab name="home" icon="fas fa-home" />
        <q-tab name="users" icon="fas fa-users" />
        <q-tab name="video" icon="ondemand_video" />
        <q-tab name="store" icon="fas fa-store" />
        <q-tab name="notification" icon="notifications" />
        <q-icon name="fas fa-bars" size="30px" class="q-mr-sm q-icon-color" />
      </q-tabs>
    </div>
    <div class="row q-pa-sm full-width">
      <q-avatar class="q-mr-sm">
        <img src="https://cdn.quasar.dev/img/avatar.png" />
      </q-avatar>
      <q-input
        rounded
        outlined
        v-model="text"
        label="No que você está pensando?"
        label-color="black"
      />
    </div>

    <div class="line q-mt-md" />
    <div class="row justify-around full-width q-pa-sm">
      <div>
        <q-icon
          color="red"
          name="fas fa-video"
          size="18px"
          class="q-mr-sm q-icon-color"
        />
        <label> Ao vivo</label>
      </div>
      <div class="vertical-line" />
      <div>
        <q-icon
          color="light-green-7"
          name="far fa-images"
          size="18px"
          class="q-mr-sm q-icon-color"
        />
        <label> Foto</label>
      </div>
      <div class="vertical-line" />
      <div>
        <q-icon
          color="purple"
          name="meeting_room"
          size="18px"
          class="q-mr-sm q-icon-color"
        />
        <label> Salas</label>
      </div>
    </div>

    <div class="line-strong q-mt-md" />
    <q-scroll-area horizontal class="container-new-room full-width">
      <div
        class="row items-center justify-between q-px-md q-py-sm no-wrap full-width container-rooms"
      >
        <div class="rounded-button row text-center q-mr-md">
          <div class="row items-center justify-center">
            <q-icon
              color="purple"
              name="fas fa-video"
              size="28px"
              class="q-mr-sm q-icon-color"
            />
          </div>
          <div class="text-left">
            <label> Criar sala</label>
          </div>
        </div>

        <q-avatar class="q-mr-sm" v-for="index in 8" :key="index">
          <img src="https://cdn.quasar.dev/img/avatar.png" />
          <q-badge color="green"></q-badge>
        </q-avatar>
      </div>
    </q-scroll-area>
    <div class="line-strong" />

    <div class="full-width q-mt-md">
      <q-scroll-area horizontal style="height: 220px">
        <div
          class="row items-center justify-between q-px-md q-py-sm no-wrap full-width container-story"
        >
          <q-img
            src="https://placeimg.com/500/300/nature"
            width="100px"
            height="200px"
            class="q-mx-sm status-item"
          >
            <q-img
              src="https://cdn.quasar.dev/img/avatar.png"
              class="q-ma-sm"
            />
          </q-img>
          <q-img
            v-for="index in 10"
            :key="index"
            src="https://placeimg.com/500/300/nature"
            width="100px"
            height="200px"
            class="q-mx-sm status-item"
          >
            <q-img
              src="https://cdn.quasar.dev/img/avatar.png"
              class="q-ma-sm"
            />
          </q-img>
        </div>
      </q-scroll-area>
    </div>
    <div class="line-strong q-mt-md" />
  </q-page>
</template>

<script>
export default {
  name: "PageIndex",
  data() {
    return {
      tab: "home",
      text: "",
    };
  },
};
</script>

<style lang="scss">
.q-tabs__content {
  height: 70px;
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
.q-tab__icon {
  font-size: 28px;
}
.q-tab {
  padding: 5px;
}
.q-tab--active {
  color: #1678f3;
}
.q-tab--inactive {
  color: #656668;
}
.q-icon-color {
  color: #656668;
}
.q-field {
  width: 82%;
}
.q-field__control {
  height: 45px;
}
.line {
  background-color: #cbced3;
  width: 100%;
  height: 1px;
}
.vertical-line {
  background-color: #cbced3;
  width: 1px;
  height: 20px;
}

.line-strong {
  background-color: #cbced3;
  width: 100%;
  height: 8px;
}

.rounded-button {
  border: 1px solid #cbced3;
  width: 110px;
  border-radius: 27px;
  padding: 4px 10px;

  div:first-child {
    width: 50%;
  }

  div {
    width: 50%;

    label {
      color: #1678f3;
    }
  }
}

.container-new-room {
  height: 70px;
}

.container-rooms {
  background-color: #fff;
}

.q-badge {
  padding: 6px;
  border-radius: 50%;
  position: absolute;
  bottom: 0px;
  right: 0px;
}
.container-story {
  .q-img {
    border-radius: 10px;
  }
}

.status-item {
  .q-img {
    border: 3px solid #1678f3;
    border-radius: 50%;
    width: 50%;
  }
}
</style>
