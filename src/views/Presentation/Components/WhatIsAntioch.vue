<script setup></script>

import ancientLibrary from "@/assets/img/ancient-library.png";

<template>
  <div class="container mt-sm-5">
    <div
      class="page-header py-6 py-md-5 my-sm-3 mb-3 border-radius-xl"
      :style="`background-image: url(${ancientLibrary})`"
      loading="lazy"
    >
      <span class="mask bg-gradient-dark"></span>
      <div class="container">
        <div class="row">
          <div class="col-lg-6 ms-lg-5">
            <h4 class="text-white">What is Antioch's mission?</h4>
            <h1 class="text-white">Preservation of history, culture, and knowledge</h1>
            <p class="lead text-white opacity-8">
              Digital media files are the modern equivalent of ancient scrolls. They contain the
              history, culture, and knowledge of our era. AntiochDAO curates and archives
              important digital media in a decentralized, robust, and economical manner.
            </p>
            <a
              class="text-white icon-move-right"
              disabled="disabled"
            >
              Read docs (coming soon)
              <i class="fas fa-arrow-right text-sm ms-1"></i>
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
