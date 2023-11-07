<template>
  <div class="container d-flex flex-column align-items-center">
    <div class="custom-flex">
      <div class="flex-column flex-width">
        <h1 class="title right-align">Dev Finder</h1>
        <form
          class="d-flex flex-column align-items-end"
          @submit.prevent="getData"
        >
          <div class="gradient-border-mask mb-4 w-75">
            <input
              v-model="pseudo"
              class="search-field w-100"
              type="text"
              placeholder="Search Github"
            />
          </div>
          <div
            class="gradient-border-mask text-center find-button mt-1"
            style="width: 160px"
          >
            <input
              type="submit"
              class="submit-button bg-transparent opacity-50"
              value="Find"
            />
          </div>
        </form>
      </div>
      <div class="align-center">
        <div class="custom-flex text-white gradient-border-mask-right">
          <div class="custom-padding flex-column">
            <div class="align-center">
              <div class="d-flex flex-column align-items-center mb-3">
                <img
                  v-if="user.avatar_url"
                  :src="user.avatar_url"
                  class="rounded-circle"
                  width="125"
                />
                <div v-else class="circle"></div>
              </div>
              <h2 class="fw-bold size">
                {{ user.name ? user.name : "Lorem ipsum" }}
              </h2>
              <p>@{{ user.login ? user.login : "lorem" }}</p>
            </div>
            <ul class="list-padding">
              <li class="mb-4 d-flex justify-content-start align-items-center">
                <Icon icon="basil:twitter-outline" width="25" />
                <div class="ms-2">
                  {{
                    user.twitter_username
                      ? user.twitter_username
                      : "Not available"
                  }}
                </div>
              </li>
              <li class="mb-4 d-flex justify-content-start align-items-center">
                <Icon icon="maki:suitcase" width="25" />
                <div class="ms-2">
                  {{ user.company ? user.company : "Not available" }}
                </div>
              </li>
              <li class="mb-4 d-flex justify-content-start align-items-center">
                <Icon icon="material-symbols:link" width="25" />
                <div class="ms-2">
                  {{ user.blog ? user.blog : "Not available" }}
                </div>
              </li>
              <li class="mb-4 d-flex justify-content-start align-items-center">
                <Icon icon="material-symbols:home" width="25" />
                <div class="ms-2">
                  {{ user.location ? user.location : "Not mentionned" }}
                </div>
              </li>
            </ul>
          </div>
          <div class="custom-padding flex-column">
            <div class="flex-row mt-5">
              <ul class="">
                <li class="stats">
                  <strong>{{
                    user.public_repos ? user.public_repos : "0"
                  }}</strong>
                  <p>Repos</p>
                </li>
                <li class="stats">
                  <strong>{{ user.followers ? user.followers : "0" }}</strong>
                  <p>Followers</p>
                </li>
                <li class="stats">
                  <strong>{{ user.following ? user.following : "0" }}</strong>
                  <p>Following</p>
                </li>
              </ul>
            </div>
            <p class="mt-4">Biography</p>
            <p class="fw-bold" style="text-align: justify">
              {{
                user.bio
                  ? user.bio
                  : "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed doeiusmod tempor incididunt ut labore et dolore magna aliqua."
              }}
            </p>
            <div class="join-date">
              <p class="mb-0">Joined on</p>
              <p>
                {{
                  user.created_at
                    ? formatDate(user.created_at)
                    : "1 January 2000"
                }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="radial-gradient mt-5"></div>
  </div>
</template>

<script>
import { Icon } from "@iconify/vue";
import axios from "axios";
export default {
  name: "App",
  components: {
    Icon,
  },
  data() {
    return { user: {}, pseudo: "" };
  },
  methods: {
    async getData() {
      try {
        const response = await axios.get(
          "https://api.github.com/users/" + this.pseudo
        );
        this.user = response.data;
      } catch (error) {
        console.log(error);
      }
    },

    formatDate(inputDate) {
      const months = [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December",
      ];

      const date = new Date(inputDate);
      const day = date.getDate();
      const month = months[date.getMonth()];
      const year = date.getFullYear();

      return `${day} ${month} ${year}`;
    },
  },
};
</script>

<style>
@font-face {
  font-family: "trykker";
  src: url("~@/assets/fonts/Trykker-Regular.ttf") format("truetype");
}
@font-face {
  font-family: "montserrat";
  src: url("~@/assets/fonts/Montserrat-VariableFont_wght.ttf")
    format("truetype");
}
/**/
ul {
  list-style: none;
}

/*default avatar*/
.circle {
  background-color: #cccccc;
  width: 125px;
  height: 125px;
  border-radius: 50%;
}

.flex-row {
  display: flex;
  flex-direction: row;
}

.flex-column {
  display: flex;
  flex-direction: column;
}

.submit-button {
  padding: 0;
  color: #fff;
  border: none;
  width: 100%;
  height: 100%;
  background-image: linear-gradient(
    93deg,
    rgba(4, 90, 64, 0.4) 0%,
    rgba(255, 255, 255, 0) 100%
  );
}
.size {
  font-size: 30px;
}

.search-field {
  background-color: transparent;
  border: none;
  color: white;
  opacity: 50%;
  padding-left: 1rem;
}

.gradient-border-mask {
  height: 30px;
  position: relative;
  padding: 1px;
}

.gradient-border-mask::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  border-radius: 50px;
  border: 2px solid transparent;
  background: linear-gradient(45deg, white, transparent) border-box;
  -webkit-mask: linear-gradient(#fff 0 0) padding-box, linear-gradient(#fff 0 0);
  mask-composite: exclude;
}

.gradient-border-mask-right {
  background: linear-gradient(
    232deg,
    rgba(4, 90, 64, 0.4) 0%,
    rgba(255, 255, 255, 0) 100%
  );
  position: relative;
  padding: 1px;
}

.gradient-border-mask-right::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  border-radius: 50px;
  border: 2px solid transparent;
  background: linear-gradient(-135deg, white, transparent) border-box;
  -webkit-mask: linear-gradient(#fff 0 0) padding-box, linear-gradient(#fff 0 0);
  mask-composite: exclude;
}

/* desktop view*/
@media (min-width: 501px) {
  #app {
    width: 100%;
    height: 100rem;
    background: linear-gradient(121deg, #045a40 0%, #043b5a 36.51%);
    font-family: "montserrat";
    padding-top: 60px;
  }
  .flex-width {
    min-width: 35%;
  }
  .radial-gradient {
    height: 56px;
    width: 82%;
    background: radial-gradient(
      50% 50% at 51.62% 50%,
      rgba(0, 0, 0, 0.4) 0%,
      rgba(0, 0, 0, 0) 100%
    );
  }
  .right-align {
    text-align: end;
  }
  .title {
    text-align: end;
    max-width: 400px;
    font-family: trykker;
    font-size: 80px;
    color: white;
    margin-bottom: 100px;
  }
  .custom-flex {
    display: flex;
    flex-direction: row;
    margin-left: 50px;
  }
  .stats {
    display: inline-block;
    margin-right: 20px;
    text-align: center;
  }
  .custom-padding {
    padding: 50px;
    align-content: center;
  }

  .join-date {
    display: inline-block;
    align-self: end;
    text-align: end;
    position: absolute;
    bottom: 0;
    margin-bottom: 50px;
  }
  .list-padding {
    padding-left: 0;
    padding-right: 20px;
  }
}
/* phone view*/
@media (max-width: 500px) {
  #app {
    width: 100%;
    height: 100%;
    background: linear-gradient(121deg, #045a40 0%, #043b5a 36.51%);
    font-family: "montserrat";
    padding-top: 40px;
    padding-left: 2%;
    padding-right: 2%;
    font-size: small;
  }
  form {
    padding-bottom: 40px;
  }

  .radial-gradient {
    visibility: hidden;
  }
  .title {
    text-align: right;
    width: 100px;
    font-family: trykker;
    font-size: large;
    color: white;
    margin-bottom: 40px;
  }
  .custom-flex {
    display: flex;
    flex-direction: column;
  }
  .stats {
    display: inline-block;
    margin-right: 10px;
    text-align: center;
  }

  .align-center {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .stat-list {
    padding-left: 0;
    display: flex;
    justify-content: center;
  }

  .custom-padding {
    padding: 10px;
  }
  .join-date {
    display: inline-block;
    align-self: center;
    text-align: center;
    bottom: 0;
    margin-bottom: 50px;
  }
}
</style>
