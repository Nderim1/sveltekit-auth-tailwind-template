<!-- src/routes/+page.svelte -->
<script lang="ts">
	import { Auth } from '@supabase/auth-ui-svelte';
	import { ThemeSupa } from '@supabase/auth-ui-shared';
	import Home from '../components/Home.svelte';

	export let data;
</script>

<svelte:head>
	<title>User Management</title>
</svelte:head>

<div class=" flex justify-center items-center h-full">
	{#if data.session}
		<Home />
	{:else}
		<div class="w-60 form-widget">
			<Auth
				supabaseClient={data.supabase}
				view="sign_in"
				redirectTo={`${data.url}/auth/callback`}
				showLinks={false}
				appearance={{ theme: ThemeSupa, style: { input: 'color: #fff' } }}
				providers={['twitter']}
			/>
		</div>
	{/if}
</div>
