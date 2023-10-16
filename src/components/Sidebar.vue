<script setup lang="ts">
import RecursiveSidebar from "./Sidebar.vue";

type Item = {
  name: string;
  items: Item[];
};

const { items } = defineProps<{
  level: number;
  items: Item[];
}>();
</script>

<template>
  <ul class="card">
    <li v-for="item in items" :key="item.name">
      <details>
        <summary class="flex group my-1 text-left max-w-xs">
          <div
            class="flex items-center cursor-pointer group-hover:bg-gray-200 rounded-full py-1 pr-4 gap-0 bg-gray-100 w-full"
            :style="{
              paddingLeft:
                item.items && item.items.length > 0
                  ? 24 * level - 16 + 'px'
                  : 24 * level + 'px',
            }"
          >
            <div v-if="item.items && item.items.length > 0">
              <svg
                class="h-4 w-4 text-gray-400"
                preserveAspectRatio="xMidYMid meet"
                viewBox="0 0 24 24"
                width="1.2em"
                height="1.2em"
              >
                <path
                  fill="none"
                  stroke="currentColor"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="m6 9l6 6l6-6"
                ></path>
              </svg>
            </div>
            <div class="font-medium pl-1 truncate group-hover:text-indigo-400">
              {{ item.name }}
            </div>
          </div>
        </summary>
        <div>
          <RecursiveSidebar
            v-if="item.items && item.items.length > 0"
            :items="item.items"
            :level="level + 1"
          />
        </div>
      </details>
    </li>
  </ul>
</template>
