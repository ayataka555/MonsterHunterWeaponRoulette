<template>
  <div class="container">
    <div class="weaponContainer">
      <div class="selectedWeaponArea">
        <p v-if="imgSrc == '' && weaponName == ''" class="initText">
          武器カテゴリを選んでください
        </p>
        <div v-else>
          <div class="weaponImgWrapper">
            <img :src="imgSrc" :alt="weaponName">
          </div>
          <p class="weaponTextWrapper">
            あなたの武器は　<span>{{ weaponName }}</span>　です！
          </p>
        </div>
      </div>
    </div>
    <div class="weaponButtonsArea">
      <button class="button" @click="guardWeaponsRondom">
        ガード可能近接武器
      </button>
      <button class="button" @click="noGuardWeaponsRondom">
        ガード不可近接武器
      </button>
      <button class="button" @click="gunsRondom">
        長距離武器
      </button>
    </div>
    <p class="footer"
      >© 2021 ayataka.juveism<br>
      twitter @ayataka_juveism
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      imgSrc: "",
      weaponName: "",
      guardWeaponsList: [
        {
          name: "大剣",
          src: require("@/assets/img/img_weapon_01.png"),
        },
        {
          name: "ランス",
          src: require("@/assets/img/img_weapon_07.png"),
        },
        {
          name: "ガンランス",
          src: require("@/assets/img/img_weapon_08.png"),
        },
        {
          name: "片手剣",
          src: require("@/assets/img/img_weapon_02.png"),
        }
      ],
      noGuardWeaponsList: [
        {
          name: "双剣",
          src: require("@/assets/img/img_weapon_03.png"),
        },
        {
          name: "操虫棍",
          src: require("@/assets/img/img_weapon_11.png"),
        },
        {
          name: "太刀",
          src: require("@/assets/img/img_weapon_04.png"),
        },
        {
          name: "ハンマー",
          src: require("@/assets/img/img_weapon_05.png"),
        },
        {
          name: "狩猟笛",
          src: require("@/assets/img/img_weapon_06.png"),
        },
        {
          name: "チャージアックス",
          src: require("@/assets/img/img_weapon_10.png"),
        },
        {
          name: "スラッシュアックス",
          src: require("@/assets/img/img_weapon_09.png"),
        }
      ],
      gunsList: [
        {
          name: "ライトボウガン",
          src: require("@/assets/img/img_weapon_13.png"),
        },
        {
          name: "ヘビィボウガン",
          src: require("@/assets/img/img_weapon_14.png"),
        },
        {
          name: "弓",
          src: require("@/assets/img/img_weapon_12.png"),
        }
      ]
    }
  },
  methods: {
    noGuardWeaponsRondom() {
      this.selectWeapon(this.noGuardWeaponsList)
    },
    gunsRondom() {
      this.selectWeapon(this.gunsList)
    },
    guardWeaponsRondom() {
      this.selectWeapon(this.guardWeaponsList)
    },
    selectWeapon(list) {
      const index = Math.floor(Math.random() * (list.length));
      const weapon = list[index];
      this.imgSrc = weapon.src
      this.weaponName = weapon.name
    }
  },
}
</script>

<style>
.container {
  padding: 40px;
  background: rgba(0, 15, 44, 0.9);
  margin: 0 auto;
  color: #fff;
  height: 100vh;
}

.selectedWeaponArea {
  height: 30vh;
}

.initText {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}

.weaponContainer {
  border-radius: 50px;
  width: 80vw;
  margin: 0 auto;
  text-align: center;
}

.weaponImgWrapper {
  padding: 40px;
  width: 200px;
  margin: 0 auto;
  background: #f9eb93;
  border-radius: 50px;
}

.weaponTextWrapper {
  margin-top: 10px;
}

.weaponButtonsArea {
  margin: 0 auto;
  width: 50vw;
}

.weaponButtonsArea > .button {
  margin-top: 20px;
}


.button {
  display: block;
  width: 100%;
  background: transparent;
  padding: 20px;
  text-align: center;
  border: 1px solid #fff;
  color:#fff;
  border-radius: 50px;
}

.footer {
  padding: 80px;
  text-align: center;
  line-height: 1.4;
}

</style>
