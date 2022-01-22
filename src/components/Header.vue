<template>
  <a-row type="flex" justify="space-between">
    <a-col :span="24">
      <a-card size="small">
        <a-row type="flex" justify="space-between" align="middle">
          <a-col :span="2">
            <div class="menu-icon">
              <MenuOutlined @click="showDrawer" id="menu-icon" />
            </div>
            <a-drawer
              :drawerStyle="getDrawerStyle"
              :bodyStyle="getBodyStyle"
              :headerStyle="getHeaderStyle"
              :width="drawerWidth"
              :title="getTitle"
              placement="left"
              :visible="visible"
              @close="onClose"
            >
              <a-card size="small" style="width: 90%">
                <a-row
                  type="flex"
                  justify="space-around"
                  align="middle"
                  @click="onClick('Home')"
                  class="menu-row"
                >
                  <a-col span="4" class="icon">
                    <HomeOutlined />
                  </a-col>
                  <a-col span="12" class="icon">
                    <a-typography-text strong>Home</a-typography-text>
                  </a-col>
                </a-row>
                <a-row
                  type="flex"
                  justify="space-around"
                  align="middle"
                  @click="onClick('Profile')"
                  class="menu-row"
                >
                  <a-col span="4" class="icon">
                    <UserOutlined />
                  </a-col>
                  <a-col span="12" class="icon">
                    <a-typography-text strong>Profile</a-typography-text>
                  </a-col>
                </a-row>
                <a-row
                  type="flex"
                  justify="space-around"
                  align="middle"
                  @click="onClick('About')"
                  class="menu-row"
                >
                  <a-col span="4" class="icon">
                    <QuestionCircleOutlined />
                  </a-col>
                  <a-col span="12" class="icon">
                    <a-typography-text strong>About</a-typography-text>
                  </a-col>
                </a-row>
              </a-card>
            </a-drawer>
          </a-col>
          <a-col :span="20">
            <a-auto-complete
              v-model:value="value"
              :options="options"
              style="width: 60%"
              placeholder="Search"
              @select="onSelect"
              @search="onSearch"
            >
              <a-input />
            </a-auto-complete>
          </a-col>
          <a-col :span="2">
            <div class="menu-icon">
              <UserOutlined @click="profileClicked" id="menu-icon" />
            </div>
          </a-col>
        </a-row>
      </a-card>
    </a-col>
  </a-row>
</template>

<script>
import {
  HomeOutlined,
  QuestionCircleOutlined,
  UsergroupAddOutlined,
  MenuOutlined,
  UserOutlined,
} from "@ant-design/icons-vue";

export default {
  name: "Header",
  data() {
    return {
      visible: false,
      windowWidth: window.innerWidth,
      value: "",
      options: null,
      allOptions: [
        {
          name: "test 1",
          value: "Bob",
        },
        {
          name: "test 2",
          value: "Walter",
        },
        {
          name: "test 3",
          value: "Frank",
        },
      ],
    };
  },
  methods: {
    showDrawer() {
      this.visible = true;
    },
    onClose() {
      this.visible = false;
    },
    onClick(target) {
      this.visible = false;
      this.$router.push({ name: target });
    },
    profileClicked() {
      this.$router.push({ name: "Profile" });
    },
    onSelect(value, option) {
      console.log("onSelect", value, option);
    },
    onSearch() {
      const list = this.allOptions.filter((option) =>
        option.value.toLowerCase().includes(this.value.toLowerCase())
      );
      this.options = list;
    },
  },
  computed: {
    drawerWidth() {
      if (this.windowWidth >= 600) {
        return this.windowWidth - this.windowWidth * 0.75;
      } else {
        return this.windowWidth - this.windowWidth * 0.3;
      }
    },
    getDrawerStyle() {
      return {
        "background-color": "#56008F",
      };
    },
    getBodyStyle() {
      return {
        color: "black",
      };
    },
    getHeaderStyle() {
      return {
        "background-color": "#56008F",
        color: "#ffffff",
      };
    },
    getTitle() {
      return (
        <a-card size="small" style="width: 90%">
          <a-row type="flex" justify="space-between" align="middle">
            <a-col span="4">
              <UsergroupAddOutlined style="fontSize: 1.2rem" />
            </a-col>
            <a-col span="16" style="fontSize: 1.2rem">
              Sponsee!
            </a-col>
          </a-row>
        </a-card>
      );
    },
  },
  components: {
    HomeOutlined,
    QuestionCircleOutlined,
    MenuOutlined,
    UserOutlined,
  },
};
</script>

<style scoped lang="scss">
@use "../base";
.ant-card {
  border: 1px solid black;
  border-radius: 12px;
  box-shadow: 6px 6px 6px 2px rgb(17, 0, 29, 0.4);
}
.ant-input {
  border: 1px solid black;
  border-radius: 12px;
}
.ant-input:focus {
  border: 1px solid black;
  border-radius: 12px;
  box-shadow: 0px 0px 4px 2px rgb(17, 0, 29, 0.4);
}
.ant-input:hover {
  border: 1px solid base.$primary-color;
}
.icon {
  font-size: 1.2rem;
  padding: 4px;
}
.menu-row:hover {
  color: base.$primary-color;
  background-color: lightslategray;
  border: 1px solid white;
  border-radius: 12px;
  box-shadow: 6px 6px 6px 2px rgb(17, 0, 29, 0.4);
  transform: translateX(8px);
}
.menu-row {
  transition: transform 250ms ease-in;
}
.menu-icon {
  font-size: 1.2rem;
}
#menu-icon:hover {
  color: base.$primary-color;
  animation-name: floating;
  animation-duration: 1s;
  animation-iteration-count: infinite;
  animation-timing-function: linear;
}

@keyframes floating {
  0% {
    transform: translate(0, 0px);
  }
  33% {
    transform: translate(0, 2px);
  }
  66% {
    transform: translate(0, -2px);
  }
  100% {
    transform: translate(0, -0px);
  }
}
</style>
