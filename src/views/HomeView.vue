<script setup lang="ts">
import { useMachine } from 'xstate-vue2'
import { createMachine } from 'xstate'

const toggleMachine = createMachine({
  id: 'toggle',
  initial: 'inactive',
  states: {
    inactive: {
      on: { TOGGLE: 'active' }
    },
    active: {
      on: { TOGGLE: 'inactive' }
    }
  }
})

const { state, send } = useMachine(toggleMachine)
</script>

<template>
  <main>
    <button @click="send('TOGGLE')">
      {{ state.value === 'inactive' ? 'Click to activate' : 'Active! Click to deactivate' }}
    </button>
  </main>
</template>
