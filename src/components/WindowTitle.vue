<template>
  <div data-tauri-drag-region class="titlebar">
    <div class="titlebar-stoplight">
      <div class="titlebar-close" @click="close">
        <svg x="0px" y="0px" viewBox="0 0 6.4 6.4">
          <polygon fill="#4d0000" points="6.4,0.8 5.6,0 3.2,2.4 0.8,0 0,0.8 2.4,3.2 0,5.6 0.8,6.4 3.2,4 5.6,6.4 6.4,5.6 4,3.2"></polygon>
        </svg>
      </div>
      <div class="titlebar-minimize" @click="minimize">
        <svg x="0px" y="0px" viewBox="0 0 8 1.1">
          <rect fill="#995700" width="8" height="1.1"></rect>
        </svg>
      </div>
      <div class="titlebar-fullscreen" @click="maximize">
        <svg class="fullscreen-svg" x="0px" y="0px" viewBox="0 0 6 5.9">
          <path fill="#006400" d="M5.4,0h-4L6,4.5V0.6C5.7,0.6,5.3,0.3,5.4,0z"></path>
          <path fill="#006400" d="M0.6,5.9h4L0,1.4l0,3.9C0.3,5.3,0.6,5.6,0.6,5.9z"></path>
        </svg>
        <svg class="maximize-svg" x="0px" y="0px" viewBox="0 0 7.9 7.9">
          <polygon fill="#006400" points="7.9,4.5 7.9,3.4 4.5,3.4 4.5,0 3.4,0 3.4,3.4 0,3.4 0,4.5 3.4,4.5 3.4,7.9 4.5,7.9 4.5,4.5"></polygon>
        </svg>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
  import { appWindow } from '@tauri-apps/api/window'

  const minimize = () => appWindow.minimize()
  const maximize = () => appWindow.maximize()
  const close = () => appWindow.close()
</script>

<style lang="scss">
.titlebar {
  display: flex;
  width: 100%;
  padding: 0 3px;
  background-color: #f6f6f6;
  .titlebar-close,
  .titlebar-minimize,
  .titlebar-fullscreen {
    float: left;
    width: 10px;
    height: 10px;
    border-radius: 50%;
    margin: 6px 4px;
    line-height: 0;
  }
  .titlebar-close {
    border: 1px solid #e2463f;
    background-color: #ff5f57;
    margin-left: 6px;
    &:active {
      border-color: #ad3934;
      background-color: #bf4943;
    }
    svg {
      width: 6px;
      height: 6px;
      margin-top: 2px;
      margin-left: 2px;
      opacity: 0;
    }
  }
  .titlebar-minimize {
    border: 1px solid #e1a116;
    background-color: #ffbd2e;
    &:active {
      border-color: #ad7d15;
      background-color: #bf9123;
    }
    svg {
      width: 8px;
      height: 8px;
      margin-top: 1px;
      margin-left: 1px;
      opacity: 0;
    }
  }
  .titlebar-fullscreen,
  .titlebar-maximize {
    border: 1px solid #12ac28;
    background-color: #28c940;
    &:active {
      border-color: #128622;
	    background-color: #1f9a31;
    }
    svg {
      &.fullscreen-svg {
        width: 6px;
        height: 6px;
        margin-top: 2px;
        margin-left: 2px;
        opacity: 0;
      }
      &.maximize-svg {
        width: 8px;
        height: 8px;
        margin-top: 1px;
        margin-left: 1px;
        opacity: 0;
        display: none;
      }
    }
  }
}
</style>