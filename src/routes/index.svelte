<script context="module" lang="ts">
	export const prerender = true;
</script>

<script lang="ts">
	import type { TopAppBarComponentDev } from '@smui/top-app-bar';
	import { Label } from '@smui/tab';
	import Content1 from "./content.svelte";
	import Drawer2 from "./drawer.svelte";
	import TopAppBar, { Row, Section, AutoAdjust } from '@smui/top-app-bar';
	let topAppBar: TopAppBarComponentDev;
	import Drawer, { AppContent, Content, Header, Title, Subtitle, Scrim } from '@smui/drawer';
	import IconButton from '@smui/icon-button';
	import ContentSvelte from './content.svelte';
	import List, { Item, Text, Graphic, Separator, Subheader } from '@smui/list';
	import { H6 } from '@smui/common/elements';
	let open = false;
	
</script>

<div class="drawer-container">
	<!-- Don't include fixed={false} if this is a page wide drawer.
		  It adds a style for absolute positioning. -->
	<Drawer variant="modal" fixed={false} bind:open>
		<Header>
			<Title>Powered by BeautiDocs</Title>
			<Subtitle>A docs platform that looks better.</Subtitle>
		</Header>
		<Content>
			<List>
				<Drawer2 />
			</List>
		</Content>
	</Drawer>

	<!-- Don't include fixed={false} if this is a page wide drawer.
		  It adds a style for absolute positioning. -->
	<Scrim fixed={false} />

	<AppContent class="app-content">
		<main class="main-content">
			<TopAppBar bind:this={topAppBar} variant="standard">
				<Row>
					<Section>
						<IconButton class="material-icons" on:click={() => (open = !open)}>menu</IconButton>
						<Title>Docs</Title>
					</Section>
				</Row>
			</TopAppBar>
			<AutoAdjust {topAppBar}>
				<ContentSvelte />
			</AutoAdjust>
		</main>
	</AppContent>
</div>

<style>
	/* Hide everything above this component. */
	:global(app),
	:global(body),
	:global(html) {
		display: block !important;
		height: auto !important;
		width: auto !important;
		position: static !important;
	}
</style>
