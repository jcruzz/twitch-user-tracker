<template>
	<div>
    <div class="user user-entry" v-if="view === 'All' || view ==='Online'" v-for="user in users">
      <img v-bind:src="user.logo">
      <p>
        <strong><a class="username" v-bind:href="twitch + user.username" target="_blank">{{ user.username }}</a></strong> -
        {{ user.stream.game }}
        <span class="user-status">
           {{ user.stream.channel.status }}
        </span>
      </p>
      <button v-on:click="deleteUser(user.username)" class="user-btn btn btn-success">Delete</button>  
    </div>
	</div>	
</template>
<script>
	export default {
		props: ['users', 'view', 'twitch'],
		methods: {
			deleteUser: function(username) {
				this.$emit('delete', username);
			}
		}
	};
</script>
<style scoped>
  .user-entry {
    background: green;
  }
  .user-entry img {
    transform: translateY(-12px);
  }
  .user-entry p {
    margin: 2% 0;
  }	
</style>