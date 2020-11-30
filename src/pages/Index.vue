<template>
  <q-page class="q-mt-sm">
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
    <Post v-for="item in post" :key="item.url" :post="item" />
  </q-page>
</template>

<script>
import Post from "../components/Post";
export default {
  name: "PageIndex",
  components: {
    Post,
  },
  data() {
    return {
      text: "",
      post: {},
    };
  },

  beforeMount() {
    this.post = [
      {
        avatar: "https://cdn.quasar.dev/img/avatar.png",
        name: "Daniel",
        time: "Ontem às 19:29",
        text:
          "Hoje o dia amanheceu assim: churrasco, alegria e família! <b>#FAMILIA</b>",
        url:
          "https://cdn.pixabay.com/photo/2017/10/03/01/12/family-2811003_960_720.jpg",
        likes: 169,
        comments: 6,
        shareds: 4,
      },
      {
        avatar: "https://cdn.quasar.dev/img/avatar.png",
        name: "Carla",
        time: "Ontem às 21:29",
        text: "Irmãos <b>#Familia</b>",
        url:
          "https://cdn.pixabay.com/photo/2014/09/23/06/04/brothers-457237_960_720.jpg",
        likes: 99,
        comments: 3,
        shareds: 6,
      },
      {
        avatar: "https://cdn.quasar.dev/img/avatar.png",
        name: "Paulo",
        time: "Ontem às 17:29",
        text: "Mãe e filha na praia.",
        url:
          "https://cdn.pixabay.com/photo/2016/11/08/05/08/adult-1807500_960_720.jpg",
        likes: 99,
        comments: 3,
        shareds: 6,
      },
      {
        avatar: "https://cdn.quasar.dev/img/avatar.png",
        name: "Lara",
        time: "Ontem às 16:29",
        text: "É incrível como eles ficaram lindos. <b>#look</b>",
        url:
          "https://cdn.pixabay.com/photo/2015/06/22/08/37/children-817365_960_720.jpg",
        likes: 299,
        comments: 43,
        shareds: 16,
      },
      {
        avatar: "https://cdn.quasar.dev/img/avatar.png",
        name: "Marcela",
        time: "Ontem às 23:29",
        text:
          "Eu e minhas irmãs no meu aniversário de 30 anos, foi só festa e alegria <b>#TRINTOU</b>",
        url:
          "https://cdn.pixabay.com/photo/2018/01/24/19/49/people-3104635_960_720.jpg",
        likes: 299,
        comments: 43,
        shareds: 16,
      },
    ];
  },
};
</script>

<style lang="scss">
.q-icon-color {
  color: #656668;
}
.q-field {
  width: 82%;
}
.q-field__control {
  height: 45px;
}

.vertical-line {
  background-color: #cbced3;
  width: 1px;
  height: 20px;
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
