<template>
  <div>
    <div class="card-select body-regular">
      <label for="camera-select">Microphone</label>
      <div id="camera-select">
        <div
          v-for="(microphone, index) in microphones"
          :key="index"
          class="option"
          v-show=" microphone.isSelected "
          @click="optionsClick"
        >
          <span>{{ microphone.name }}</span>
          <svg viewBox="0 0 18 18" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path
              fill-rule="evenodd"
              clip-rule="evenodd"
              d="M9.00002 12.75C8.62052 12.75 8.25752 12.5752 8.00552 12.2685L4.84577 8.445C4.46777 7.98675 4.39202 7.3365 4.65152 6.78675C4.88027 6.3015 5.33552 6 5.84027 6H12.1598C12.6645 6 13.1198 6.3015 13.3485 6.78675C13.608 7.3365 13.5323 7.98675 13.155 8.44425L9.99452 12.2685C9.74252 12.5752 9.37952 12.75 9.00002 12.75Z"
              fill="#222222"
            ></path>
            <mask
              id="mask0"
              mask-type="alpha"
              maskUnits="userSpaceOnUse"
              x="4"
              y="6"
              width="10"
              height="7"
            >
              <path
                fill-rule="evenodd"
                clip-rule="evenodd"
                d="M9.00002 12.75C8.62052 12.75 8.25752 12.5752 8.00552 12.2685L4.84577 8.445C4.46777 7.98675 4.39202 7.3365 4.65152 6.78675C4.88027 6.3015 5.33552 6 5.84027 6H12.1598C12.6645 6 13.1198 6.3015 13.3485 6.78675C13.608 7.3365 13.5323 7.98675 13.155 8.44425L9.99452 12.2685C9.74252 12.5752 9.37952 12.75 9.00002 12.75Z"
                fill="white"
              ></path>
            </mask>
            <g mask="url(#mask0)"></g>
          </svg>
        </div>
      </div>
    </div>
    <transition name="optiondropdown">
      <ul v-if="optionsclicked" class="options">
        <li
          v-if="microphone.isSelected == false"
          v-for="(microphone, index) in microphones"
          :key="index"
          @click="optionsBlur"
        >
          <span>{{ microphone.name }}</span>
        </li>
      </ul>
    </transition>

    <span v-show="optionsclicked" @click="optionsBlur" class="option-blur"></span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      optionsclicked: false,

      microphones: [
        {
          name: "Built-in Microphone (E...asfdsdfsd",
          isSelected: true
        },
        {
          name: "option 2",
          isSelected: false
        },
        {
          name: "option 3",
          isSelected: false
        },
        {
          name: "option 4",
          isSelected: false
        }
      ]
    };
  },

  methods: {
    optionsClick() {
      if (this.optionsclicked == false) {
        this.optionsclicked = true;
      } else {
        this.optionsclicked = false;
      }
    },
    optionsBlur() {
      this.optionsclicked = false;
    }
  }
};
</script>

<style lang="scss">
//variables

@import "../assets/scssvariables.scss";

.card-select {
  display: flex;
  flex-direction: row;
  height: 48px;
  width: 100%;

  align-items: center;

  label {
    min-width: 100px !important;
    height: 18px;
    display: flex;
    align-items: center;
  }
  .option {
    display: flex;
    width: 236px;
    height: 48px !important;
    border-radius: $radius-2;
    padding: 0px 16px;
    align-items: center;
    border: $br-normal;
    justify-content: space-between;
    cursor: pointer;
    position: relative;
    span {
      display: flex;
      overflow: hidden;
      white-space: nowrap;
      max-width: 80%;
    }
    svg {
      width: 18px;
      height: 18px;
    }
  }

  .option:hover {
    background-color: $grey-10;
    svg {
      background-color: $grey-40;
      border-radius: 100%;
    }
  }
}

.options {
  position: absolute;
  right: 24px;
  display: flex;
  flex-direction: column;
  width: 236px;
  z-index: 301;
  border-radius: $radius-2;

  align-items: center;
  background-color: $light;
  border: $br-normal;
  border-top: none;
  justify-content: space-between;
  cursor: pointer;
  list-style-type: none;
  box-shadow: $shadow-1;

  li {
    width: 100%;
    height: 48px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-bottom: $br-normal;

    span {
      display: flex;
      overflow: hidden;
      white-space: nowrap;
      max-width: 80%;
    }
  }

  li:last-child {
    border: transparent 1px solid !important;
    border-radius: 0 0 8px 8px;
  }

  li:first-child {
    border-radius: 8px;
  }

  li:hover {
    background-color: $grey-10;
  }
}

.option-blur {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  z-index: 100;
}

.optiondropdown-enter-active {
  transform-origin: top;

  animation: scale-toptobottom 0.5s;
}
.optiondropdown-leave-active {
  transform-origin: top;

  animation: scale-toptobottom 0.5s reverse;
}

@keyframes scale-toptobottom {
  0% {
    transform: scaleY(0);
  }

  100% {
    transform: scaleY(1);
  }
}
</style>
