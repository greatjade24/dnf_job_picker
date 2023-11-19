<script lang="ts" setup>
    import { JOB } from "~/config/job"

    function randomNum(max: number): string {
        return (Math.floor(Math.random() * max)).toString()
    }

    const finalJob = ref<string>()

    const chooseJob = () => {
        let code = 0

        while(true) {
            const character = randomNum(17)
            const job = randomNum(5)

            code = parseInt(character + job)

            if (JOB[code]) {
                finalJob.value = JOB[code]

                break
            }
        }

    }
</script>

<template>
    <div>
        <div>
            <span class="h1">직업 추첨기 </span>
            <button v-on:click="chooseJob" class="choice-button">뽑기</button>
        </div>
        <br/>
        <div class="job-box">
            <span class="show-room">{{ finalJob || '' }}</span>
        </div>
    </div>
</template>

<style scoped>
    .job-box {
        border: 2px solid black;
        width: 33rem;
        height: 50vh;

        text-align: center;
    }

    .h1 {
        font-size: 30px;
        font-weight: bold;
    }

    .choice-button {
        width: 50px;
        margin-bottom: 12px;
        line-height: 30px;
    }

    .show-room {
        position: relative;
        font-size: 33px;
        line-height: 20rem;
    }
</style>