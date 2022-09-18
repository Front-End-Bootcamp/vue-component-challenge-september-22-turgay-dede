<template>
	<el-row>
		<el-col
			v-for="group in props.groups"
			:key="group"
			:span="8"
		>
			<el-card :body-style="[ selectedGroup === group ? { background: selectedGroup, color: 'white' } : {background: 'aliceblue' , color: 'black'} ] ">
				<p>{{ group }}</p>
				<div style="padding: 14px">
					<div class="bottom">
						<el-button text class="button" @click="groupMemberHandler(group)">Get {{ group }} Members</el-button>
					</div>
				</div>
			</el-card>
		</el-col>
	</el-row>
</template>

<script setup>
import { ref } from "vue";

const props = defineProps(["groups"])
const emits = defineEmits(["getGroupMembers"])
const selectedGroup = ref('')

function groupMemberHandler(group){
	emits("getGroupMembers",group)
	selectedGroup.value = group
}

</script>

<style>

.bottom {
	margin-top: 13px;
	line-height: 12px;
	display: flex;
	justify-content: space-between;
	align-items: center;
}

.button {
	padding: 0;
	min-height: auto;
}

</style>
