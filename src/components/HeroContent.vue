<template>
  <div class="w-full max-w-6xl mx-auto px-4 pb-12">
    <h1 class="text-center font-bold text-2xl md:text-3xl my-12">
      Assets untuk materi Pengenalan Dasar Figma
    </h1>

    <div class="grid grid-cols-1 md:grid-cols-2 gap-8 mb-16">
      <!-- Left Column -->
      <div class="flex flex-col">
        <h2 class="font-bold text-lg mb-4">Gambar Untuk Hero Section</h2>
        <div class="relative group rounded-lg overflow-hidden shadow-md h-full">
          <img
            ref="heroImg"
            src="/assets/img/sekolah.jpg"
            alt="Hero Section"
            class="w-full h-full object-cover"
            crossorigin="anonymous"
          />
          <button
            @click="copyImage('hero')"
            class="absolute top-3 right-3 bg-[#00ADB5] hover:bg-[#009ba3] text-white px-4 py-2 rounded-lg font-semibold text-sm opacity-0 group-hover:opacity-100 transition-opacity duration-200 shadow-lg cursor-pointer"
          >
            {{ copiedItem === 'hero' ? 'Copied!' : 'Copy Gambar' }}
          </button>
        </div>
      </div>

      <!-- Right Column -->
      <div class="flex flex-col gap-8">
        <div>
          <h2 class="font-bold text-lg mb-4">Gambar Untuk Berita</h2>
          <div class="relative group rounded-lg overflow-hidden shadow-md">
            <img
              ref="beritaImg"
              src="/assets/img/berita.jpg"
              alt="Berita"
              class="w-full h-auto object-cover"
              crossorigin="anonymous"
            />
            <button
              @click="copyImage('berita')"
              class="absolute top-3 right-3 bg-[#00ADB5] hover:bg-[#009ba3] text-white px-4 py-2 rounded-lg font-semibold text-sm opacity-0 group-hover:opacity-100 transition-opacity duration-200 shadow-lg cursor-pointer"
            >
              {{ copiedItem === 'berita' ? 'Copied!' : 'Copy Gambar' }}
            </button>
          </div>
        </div>
        <div>
          <h2 class="font-bold text-lg mb-4">Gambar Untuk Maps</h2>
          <div class="relative group rounded-lg overflow-hidden shadow-md">
            <img
              ref="mapsImg"
              src="/assets/img/maps.png"
              alt="Maps"
              class="w-full h-auto object-cover"
              crossorigin="anonymous"
            />
            <button
              @click="copyImage('maps')"
              class="absolute top-3 right-3 bg-[#00ADB5] hover:bg-[#009ba3] text-white px-4 py-2 rounded-lg font-semibold text-sm opacity-0 group-hover:opacity-100 transition-opacity duration-200 shadow-lg cursor-pointer"
            >
              {{ copiedItem === 'maps' ? 'Copied!' : 'Copy Gambar' }}
            </button>
          </div>
        </div>
      </div>
    </div>

    <!-- Colors Section -->
    <div class="flex flex-col items-center mb-12">
      <h2 class="font-bold text-xl mb-12">Warna Untuk Desain Website</h2>
      <div
        class="flex flex-col md:flex-row justify-center items-start gap-8 md:gap-24 w-full max-w-4xl"
      >
        <!-- Color Item 1 -->
        <div class="flex flex-col items-center gap-4">
          <div class="relative group">
            <div class="w-20 h-20 bg-[#222831] shadow-sm rounded-lg"></div>
            <button
              @click="copyText('#222831')"
              class="absolute -bottom-2 left-1/2 transform -translate-x-1/2 bg-[#00ADB5] hover:bg-[#009ba3] text-white px-3 py-1 rounded-md font-semibold text-xs opacity-0 group-hover:opacity-100 transition-opacity duration-200 shadow-lg cursor-pointer whitespace-nowrap"
            >
              {{ copiedItem === '#222831' ? 'Copied!' : 'Copy' }}
            </button>
          </div>
          <span class="font-bold text-lg">Warna Teks</span>
          <code class="bg-gray-100 px-2 py-1 rounded text-sm font-mono">#222831</code>
        </div>

        <!-- Color Item 2 -->
        <div class="flex flex-col items-center gap-4">
          <div class="relative group">
            <div class="w-20 h-20 bg-[#00ADB5] shadow-sm rounded-lg"></div>
            <button
              @click="copyText('#00ADB5')"
              class="absolute -bottom-2 left-1/2 transform -translate-x-1/2 bg-[#222831] hover:bg-[#1a1f26] text-white px-3 py-1 rounded-md font-semibold text-xs opacity-0 group-hover:opacity-100 transition-opacity duration-200 shadow-lg cursor-pointer whitespace-nowrap"
            >
              {{ copiedItem === '#00ADB5' ? 'Copied!' : 'Copy' }}
            </button>
          </div>
          <span class="font-bold text-lg">Warna Button</span>
          <code class="bg-gray-100 px-2 py-1 rounded text-sm font-mono">#00ADB5</code>
        </div>

        <!-- Color Item 3 -->
        <div class="flex flex-col items-center gap-4">
          <div class="relative group">
            <div class="w-20 h-20 bg-[#EEEEEE] shadow-sm border border-gray-200 rounded-lg"></div>
            <button
              @click="copyText('#EEEEEE')"
              class="absolute -bottom-2 left-1/2 transform -translate-x-1/2 bg-[#00ADB5] hover:bg-[#009ba3] text-white px-3 py-1 rounded-md font-semibold text-xs opacity-0 group-hover:opacity-100 transition-opacity duration-200 shadow-lg cursor-pointer whitespace-nowrap"
            >
              {{ copiedItem === '#EEEEEE' ? 'Copied!' : 'Copy' }}
            </button>
          </div>
          <span class="font-bold text-lg">Warna Background</span>
          <code class="bg-gray-100 px-2 py-1 rounded text-sm font-mono">#EEEEEE</code>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const copiedItem = ref<string | null>(null)
const heroImg = ref<HTMLImageElement | null>(null)
const beritaImg = ref<HTMLImageElement | null>(null)
const mapsImg = ref<HTMLImageElement | null>(null)

const copyText = async (text: string) => {
  try {
    await navigator.clipboard.writeText(text)
    copiedItem.value = text
    setTimeout(() => {
      copiedItem.value = null
    }, 2000)
  } catch (err) {
    console.error('Failed to copy:', err)
  }
}

const copyImage = async (imageKey: string) => {
  const imgRefs: Record<string, HTMLImageElement | null> = {
    hero: heroImg.value,
    berita: beritaImg.value,
    maps: mapsImg.value,
  }

  const img = imgRefs[imageKey]
  if (!img) return

  try {
    const canvas = document.createElement('canvas')
    canvas.width = img.naturalWidth
    canvas.height = img.naturalHeight
    const ctx = canvas.getContext('2d')
    if (!ctx) return

    ctx.drawImage(img, 0, 0)

    canvas.toBlob(async (blob) => {
      if (!blob) return
      try {
        await navigator.clipboard.write([
          new ClipboardItem({
            'image/png': blob,
          }),
        ])
        copiedItem.value = imageKey
        setTimeout(() => {
          copiedItem.value = null
        }, 2000)
      } catch (err) {
        console.error('Failed to copy image:', err)
      }
    }, 'image/png')
  } catch (err) {
    console.error('Failed to copy image:', err)
  }
}
</script>
