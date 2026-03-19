<template>
  <div class="auth-layout">
    <!-- 左侧：品牌/氛围区 -->
    <div class="left-hero">
      <el-image
          class="hero-img"
          fit="cover"
          src="/OIP.jpg"
      />
      <div class="hero-overlay"></div>
      <div class="hero-grid"></div>

      <!-- 极简文案 -->
      <div class="welcome-title">
        <div class="welcome-badge">Console</div>
        <div class="welcome-head">服务器管理平台</div>
        <div class="welcome-sub">安全 · 可观测 · 高效</div>
      </div>
    </div>

    <!-- 右侧：登录区 -->
    <div class="right-card">
      <div class="right-card-inner">
        <router-view v-slot="{ Component }">
          <transition name="el-fade-in-linear" mode="out-in">
            <component :is="Component" class="route-host" />
          </transition>
        </router-view>
      </div>
    </div>
  </div>
</template>

<script setup>
</script>

<style scoped>
/* ====== Layout ====== */
.auth-layout {
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  display: flex;
  background: #0b0f1a;
}

/* ====== Left Hero ====== */
.left-hero {
  position: relative;
  flex: 1;
  overflow: hidden;
  min-width: 0;
}

.hero-img {
  width: 100%;
  height: 100%;
  transform: scale(1.03);
  filter: saturate(0.95) contrast(1.08) brightness(0.95);
}

/* 冷静的控制台遮罩 */
.hero-overlay {
  position: absolute;
  inset: 0;
  background:
      radial-gradient(900px 600px at 20% 80%, rgba(80, 140, 255, 0.16), transparent 60%),
      linear-gradient(135deg, rgba(0,0,0,0.55) 0%, rgba(0,0,0,0.18) 45%, rgba(0,0,0,0.65) 100%);
  pointer-events: none;
}

/* 微弱网格科技感（不会喧宾夺主） */
.hero-grid {
  position: absolute;
  inset: 0;
  background-image:
      linear-gradient(rgba(255,255,255,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(255,255,255,0.04) 1px, transparent 1px);
  background-size: 32px 32px;
  opacity: 0.35;
  pointer-events: none;
}

/* ====== Welcome Text (Minimal) ====== */
.welcome-title {
  position: absolute;
  left: 56px;
  bottom: 64px;
  color: #fff;
  text-shadow: 0 8px 26px rgba(0, 0, 0, 0.6);
}

.welcome-badge {
  display: inline-block;
  padding: 6px 10px;
  font-size: 10px;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.10);
  border: 1px solid rgba(255, 255, 255, 0.16);
  backdrop-filter: blur(6px);
  margin-bottom: 12px;
}

.welcome-head {
  font-size: 34px;
  font-weight: 800;
  line-height: 1.1;
  margin-bottom: 10px;
}

.welcome-sub {
  font-size: 13.5px;
  letter-spacing: 0.06em;
  opacity: 0.9;
}

/* ====== Right Card ====== */
.right-card {
  width: 420px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 40px 32px;

  background-color: var(--el-bg-color);
  background-image:
      linear-gradient(180deg, rgba(255, 255, 255, 0.03), rgba(255, 255, 255, 0.01));

  border-left: 1px solid rgba(255, 255, 255, 0.06);
  box-shadow:
      -24px 0 80px rgba(0, 0, 0, 0.35),
      -2px 0 0 rgba(255, 255, 255, 0.02);
  z-index: 2;
}

/* 登录区内层：更像“安全入口” */
.right-card-inner {
  width: 100%;
  max-width: 360px;
  padding: 28px 24px;
  border-radius: 16px;

  background:
      linear-gradient(135deg, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0.015));
  border: 1px solid rgba(255, 255, 255, 0.06);
  backdrop-filter: blur(10px);

  box-shadow:
      0 18px 50px rgba(0, 0, 0, 0.28),
      inset 0 1px 0 rgba(255, 255, 255, 0.05);
}

.route-host {
  height: 100%;
}

/* ====== Responsive ====== */
@media (max-width: 960px) {
  .left-hero {
    display: none;
  }

  .right-card {
    width: 100%;
    border-left: none;
    box-shadow: none;
  }

  .right-card-inner {
    max-width: 420px;
  }
}
</style>
