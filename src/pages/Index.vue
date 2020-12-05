<template>
  <q-page class="q-mt-sm">
    <div class="row q-pa-sm full-width">
      <q-avatar class="q-mr-sm">
        <img src="https://cdn.quasar.dev/img/avatar.png" />
      </q-avatar>
      <q-input
        rounded
        outlined
        @click="open()"
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
      <div @click="open">
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
    <Post v-for="item in post" :key="item.id" :post="item" />

    <q-dialog
      v-model="dialog"
      position="bottom"
      full-height
      full-width
      maximized
    >
      <q-card>
        <div
          class="q-ma-md q-pa-sm row items-center justify-between full-width"
        >
          <div>
            <q-icon
              name="arrow_back"
              size="23px"
              class="q-mr-sm"
              @click="dialog = false"
            ></q-icon>
            <span>Criar publicação</span>
          </div>
          <span
            @click="sendPost"
            class="q-mr-sm"
            :class="imagePreview !== '' ? 'text-blue' : 'text-grey'"
            >PUBLICAR</span
          >
          <div class="line q-mt-md"></div>
        </div>
        <div class="row q-ma-md">
          <q-avatar class="q-mr-sm">
            <img src="https://cdn.quasar.dev/img/avatar.png" />
          </q-avatar>
          <div class="column">
            <strong>Daniel Lopes</strong>
            <div class="row">
              <div
                class="custom-button row items-center justify-around q-mr-sm"
              >
                <q-icon name="fas fa-globe-asia" size="12px"></q-icon>
                <strong> Público</strong>
                <q-icon name="arrow_drop_down" size="25px"></q-icon>
              </div>
              <div class="custom-button row items-center justify-around">
                <q-icon name="add" size="12px"></q-icon>
                <strong> Álbum</strong>
                <q-icon name="arrow_drop_down" size="25px"></q-icon>
              </div>
            </div>
          </div>
        </div>
        <q-input
          v-model="text"
          filled
          class="custom-textarea full-width"
          :placeholder="
            imagePreview === ''
              ? 'No que você está pensando?'
              : 'Dia algo sobre essa foto...'
          "
          label-color="grey-5"
          :type="imagePreview === '' ? 'textarea' : 'text'"
          rows="20"
          bg-color="white"
        >
        </q-input>
        <q-img v-if="imagePreview !== ''" :src="imagePreview" :ratio="1">
        </q-img>

        <q-card-section class="row items-center no-wrap">
          <div>
            <div class="text-black">Adicionar à sua publicação</div>
          </div>

          <q-space />

          <div class="row justify-between items-center" style="width: 30%">
            <q-icon
              name="video_call"
              size="28px"
              color="purple"
              @click="openUpload()"
            />
            <q-icon color="light-green-7" name="far fa-images" size="20px" />
            <q-icon color="blue" name="person" size="25px" />
            <q-icon color="orange-6" name="insert_emoticon" size="25px" />
          </div>
        </q-card-section>
      </q-card>
    </q-dialog>
    <q-file v-model="file" label="Standard" id="fileUpload" v-show="false" />
  </q-page>
</template>

<script>
import Post from "../components/Post";
import api from "../services/api";
export default {
  name: "PageIndex",
  components: {
    Post,
  },
  data() {
    return {
      text: "",
      post: {},
      dialog: false,
      file: [],
      imagePreview: "",
    };
  },
  methods: {
    open() {
      this.dialog = true;
    },
    close() {
      this.dialog = false;
    },
    triggerNegative() {
      this.$q.notify({
        type: "negative",
        position: "top",
        message: `Você precisa adicionar uma imagem`,
      });
    },

    async sendPost() {
      if (this.imagePreview === "") {
        this.triggerNegative();
        return;
      }
      const body = {
        text: this.text,
        picture: this.imagePreview,
      };

      await api
        .post("post", body, {})
        .then((response) => {
          console.log(response.data);
          if (response.data) {
            console.log("here");
            this.post = [...this.post, response.data];
            this.close();
          }
        })
        .catch((error) => {
          console.log(error);
        });
    },
    openUpload() {
      document.querySelector(".q-field__input").click();
    },
  },
  watch: {
    async file() {
      var formData = new FormData();
      formData.append("image", this.file);

      await api
        .post("upload", formData, {
          headers: {
            "Content-Type": "multipart/form-data",
          },
        })
        .then((response) => {
          this.imagePreview = "http://localhost:3000/" + response.data.image;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
  async beforeMount() {
    await api
      .get("post", {})
      .then((response) => {
        this.post = response.data;
      })
      .catch((error) => {
        console.log(error);
      });
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

.custom-button {
  width: 90px;
  height: 30px;
  padding: 2px;
  font-size: 12px !important;
  border: 1px solid #e5e5e5;
  border-radius: 7px;
  cursor: pointer;

  .q-icon {
    color: #969393;
  }
  strong {
    color: #969393;
  }
}

.custom-textarea {
  font-size: 20px;
  padding: 10px;
  .q-field__control {
    padding: 0px;
  }

  .q-field__control-container {
    background-color: white;
    display: flex;
    flex-direction: column;
  }
  .q-placeholder {
    background-color: white;
  }
}
</style>
