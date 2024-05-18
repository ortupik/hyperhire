<template>
    <q-header  class="transparent-bg hyperhire-header">
      <q-toolbar class="hyperhire-toolbar ">
        <q-toolbar-title class="hyperhire-logo">
          <img src="logo-light.png" alt="Hyperhire Logo" />
          <span class="title">hyperhire</span>
        </q-toolbar-title>

        <div class="menus gt-xs">
          <q-btn flat no-caps label="채용" class="menu-item" icon-right="expand_more" color="#4a77ff" />
          <span class="menu-item">해외 개발자 활용 서비스</span>
        </div>

        <q-space />

        <q-btn class="inquiry-button" no-caps label="문의하기" text-color="#4a77ff" />

      </q-toolbar>

    </q-header>
</template>

<script>
export default {
 
};
</script>


<style lang="scss" scoped>

.transparent-bg {
  background: transparent !important; // Override default background
}
.hyperhire-header {
 height: 60px;
 position: relative;
}

.hyperhire-toolbar {
  height: 100%;
}

.hyperhire-logo {
  img {
    max-height: 20px;
  }
}

.title {
  font-size: 18px;
  padding-left: 6px;
}

.menus {
  display: flex;
  align-items: center;
  gap: 20px;
}

.menu-item {
  font-size: 1em;
  color: white;
}

.inquiry-button {
  border: 1px solid white;
  background: white;
  color: #4a77ff;
  padding: 0 20px;
  font-weight:900;

  &:hover {
    background: rgba(255, 255, 255, 0.1);
  }
}
</style>
