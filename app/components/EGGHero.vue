<template>
  <section class="relative isolate overflow-hidden bg-slate-900 
    [mask-image:linear-gradient(to_bottom,black_80%,transparent)]">
    <!-- Background Image -->
    <img
      src="/images/eeg-hero.jpg"
      alt="EEG waveform visualization"
      class="absolute inset-0 -z-10 h-full w-full object-cover"
    />

    <!-- Washed overlay -->
    <div class="absolute inset-0 -z-10 bg-slate-900/70 backdrop-blur-[2px]" />

    <!-- Content -->
    <div class="mx-10 max-w-7xl px-6 py-32 sm:py-40 lg:px-8">
        <p class="text-sm font-semibold font-secondary uppercase tracking-[0.3em] text-primary">
          EEG-Based Alzheimer’s Screening
        </p>

        <h1 class="mt-6 text-4xl font-semibold font-primary tracking-tight text-white sm:text-6xl">
          Alzheimer's Slot Machine
        </h1>

        <p class="mt-6 text-lg font-secondary leading-8 text-slate-300">
          Upload EEG data and detect Alzheimer's Disease using our AI-Powered tool.
        </p>

        <div class="mt-10 flex flex-col items-center gap-4 sm:flex-row sm:justify-center">
          <SMButton
            size="xl"
            text="Start Now"
          >
          </SMButton>
        </div>
    </div>
  </section>
</template>