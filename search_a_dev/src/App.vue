<template>
  <div class="container d-flex flex-column align-items-center">
    <div class="custom-flex">
      <div class="flex-column flex-width">
        <h1 class="title right-align">Dev Finder</h1>
        <form class="d-flex flex-column align-items-end">
          <div class="gradient-border-mask mb-4 w-75">
            <input
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
              id="find-dev"
              type="submit"
              class="submit-button bg-transparent"
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
                  src="@/assets/logo.png"
                  class="rounded-circle"
                  width="125"
                />
              </div>
              <h2 class="fw-bold">The octocat</h2>
              <p>@octocat</p>
            </div>
            <ul>
              <li class="mb-4 d-flex justify-content-start align-items-center">
                <Icon icon="basil:twitter-outline" width="25" />
                <div class="ms-2">Not available</div>
              </li>
              <li class="mb-4 d-flex justify-content-start align-items-center">
                <Icon icon="maki:suitcase" width="25" />
                <div class="ms-2">@github</div>
              </li>
              <li class="mb-4 d-flex justify-content-start align-items-center">
                <Icon icon="material-symbols:link" width="25" />
                <div class="ms-2">https://github.blog</div>
              </li>
              <li class="mb-4 d-flex justify-content-start align-items-center">
                <Icon icon="material-symbols:home" width="25" />
                <div class="ms-2">San Francisco</div>
              </li>
            </ul>
          </div>
          <div class="custom-padding flex-column">
            <div class="flex-row mt-5">
              <ul class="">
                <li class="stats">
                  <strong>8</strong>
                  <p>Repos</p>
                </li>
                <li class="stats">
                  <strong>7665</strong>
                  <p>Followers</p>
                </li>
                <li class="stats">
                  <strong>9</strong>
                  <p>Following</p>
                </li>
              </ul>
            </div>
            <p class="mt-4">Biography</p>
            <p class="fw-bold" style="text-align: justify">
              Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
              eiusmod tempor incididunt ut labore et dolore magna aliqua.
            </p>
            <div class="join-date">
              <p class="mb-0">Joined on</p>
              <p>25 January 2011</p>
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
export default {
  name: "App",
  components: {
    Icon,
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
ul {
  list-style: none;
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

#find-dev:hover {
}

@media (min-width: 501px) {
  #app {
    width: 100%;
    height: 100%;
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
}

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
    font-size: 10px;
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
  max-height: 30px;
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
  max-height: initial;
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
</style>
