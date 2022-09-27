<template>
    <div>
        <!-- slot is used when u want to make it a wrapper component, any markup passed between will go here, it can be multiple my naming them -->
        <slot></slot>
    </div>
</template>

<style scoped>
    div {
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  margin: 2rem auto;
  max-width: 40rem;
}
</style>