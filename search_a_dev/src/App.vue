<template>
  <div class="container d-flex flex-column align-items-center">
    <div class="flex-row">
      <div class="flex-column">
        <h1 class="title">Dev Finder</h1>
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
      <div>
        <div
          class="flex-row ms-5 text-white gradient-border-mask-right"
          style="max-width: 89%"
        >
          <div class="p-5 flex-column">
            <div>
              <img src="@/assets/logo.png" />
            </div>
            <h2 class="fw-bold">The octocat</h2>
            <p>@octocat</p>
            <ul>
              <li class="mb-4 d-flex justify-content-start align-items-center">
                <Icon icon="basil:twitter-outline" />
                <div class="ms-2">Not available</div>
              </li>
              <li class="mb-4 d-flex justify-content-start align-items-center">
                <Icon icon="maki:suitcase" />
                <div class="ms-2">@github</div>
              </li>
              <li class="mb-4 d-flex justify-content-start align-items-center">
                <Icon icon="material-symbols:link" />
                <div class="ms-2">https://github.blog</div>
              </li>
              <li class="mb-4 d-flex justify-content-start align-items-center">
                <Icon icon="material-symbols:home" />
                <div class="ms-2">San Francisco</div>
              </li>
            </ul>
          </div>
          <div class="p-5 flex-column">
            <div class="flex-row mt-5">
              <ul>
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
            <div
              class="align-self-end position-absolute bottom-0 mb-5"
            >
              <p>Joined on</p>
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


.stats {
  display: inline-block;
  margin-right: 40px;
  text-align: center;
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

.radial-gradient {
  height: 56px;
  width: 82%;
  background: radial-gradient(
    50% 50% at 51.62% 50%,
    rgba(0, 0, 0, 0.4) 0%,
    rgba(0, 0, 0, 0) 100%
  );
}

.title {
  text-align: right;
  width: 442px;
  font-family: trykker;
  font-size: 100px;
  color: white;
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
  max-width: 100%;
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

#app {
  width: 100%;
  height: 100%;
  background: linear-gradient(121deg, #045a40 0%, #043b5a 36.51%);
  font-family: "montserrat";
  padding-top: 60px;
}
</style>
