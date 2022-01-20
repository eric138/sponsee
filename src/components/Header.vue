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
                    <HomeFilled />
                  </a-col>
                  <a-col span="12" class="icon">
                    <a-typography-text strong>Home</a-typography-text>
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
                    <QuestionCircleFilled />
                  </a-col>
                  <a-col span="12" class="icon">
                    <a-typography-text strong>About</a-typography-text>
                  </a-col>
                </a-row>
              </a-card>
            </a-drawer>
          </a-col>
          <a-col :span="20">
            <div>hello</div>
          </a-col>
          <a-col :span="2">
            <div class="menu-icon">
              <UserOutlined id="menu-icon" />
            </div>
          </a-col>
        </a-row>
      </a-card>
    </a-col>
  </a-row>
</template>

<script>
import {
  HomeFilled,
  QuestionCircleFilled,
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
    HomeFilled,
    QuestionCircleFilled,
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
.icon {
  font-size: 1.2rem;
  padding: 4px;
}
.menu-icon {
  font-size: 1.2rem;
}
#menu-icon:hover {
  color: base.$primary-color;
}
</style>
