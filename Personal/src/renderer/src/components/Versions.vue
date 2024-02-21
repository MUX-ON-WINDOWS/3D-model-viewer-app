<script>
import Navigation from '../components/Navigation.vue';

</script>
<template>
  <div class="ContainerSettings">
    <Navigation />
    <div class="ContainerSettingContent">
      <h1>Settings</h1>
      <p>Current theme source: <strong id="theme-source">System</strong></p>

      <button id="toggle-dark-mode">Theme Switch</button>
    </div>
  </div>
</template>

<script setup>
import { onMounted } from 'vue';

const toggleDarkMode = async () => {
  const isDarkMode = await window.darkMode.toggle();
  document.getElementById('theme-source').innerHTML = isDarkMode ? 'Dark' : 'Light';
};

const resetToSystemTheme = async () => {
  await window.darkMode.system();
  document.getElementById('theme-source').innerHTML = 'System';
};

onMounted(() => {
  document.getElementById('toggle-dark-mode').addEventListener('click', toggleDarkMode);
  document.getElementById('reset-to-system').addEventListener('click', resetToSystemTheme);
});
</script>
