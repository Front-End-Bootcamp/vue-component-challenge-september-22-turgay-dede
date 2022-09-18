<script setup>
import Card from "./components/Card.vue"
import DATA from "../assets/data/data.json"
import {onMounted, ref} from "vue";
import GroupMembers from "@/components/GroupMembers.vue";

let groups = ref([])
let members = ref([])
onMounted(() => {
	let groupsName = DATA.map(d => d.group)
	groups.value = [...new Set(groupsName)]
})

function getGroupMembers(groupName) {
	members.value = DATA.filter(d => d.group === groupName)
}
</script>

<template>
	<Card :groups="groups" @getGroupMembers="getGroupMembers"></Card>
	<GroupMembers class="members" :members="members"></GroupMembers>
</template>

<style scoped>
.members {
	top: 50px;
}
</style>
