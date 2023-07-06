<script setup lang="ts">

const value = ref<string>('')
const props = defineProps<{ id: number }>()
const { data, pending } = useAsyncData('data', () => resolveData(), { watch: [() => props.id, () => value.value] });

const sleep = (ms: number) => new Promise(resolve => setTimeout(resolve, ms))

async function resolveData() {
    console.log('resolveData', props.id, value.value)
    await sleep(1000)
    return {
        id: props.id,
        value: value.value,
        message: 'Hello World!',
        timeStamp: new Date().toISOString()
    }
}
</script>

<template>
    <div>
        <input type="text" v-model="value">
        {{ pending ? 'pending' : 'resolved'  }}
        <pre>
            {{  data }}
        </pre>
    </div>
</template>