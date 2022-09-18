<template>
	<el-row class="memberCard">
		<el-col
			v-for="member in props.members"
			:key="member.id"
			:span="8"
		>
			<el-card :body-style="[ member.type != null ? { background: member.group} : {background: 'white'} ] ">
				<p>{{ member.name }}</p>
				<div style="padding: 14px">
					<span>Type: {{ member.type !== null ? "Assistant" : "Student" }}</span>
				</div>
			</el-card>
		</el-col>
	</el-row>
</template>

<script setup>
const props = defineProps(["members"])

</script>
