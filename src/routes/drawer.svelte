
<script lang="ts">
    import { Item, Graphic, Text, Separator, Subheader } from "@smui/list";
    import { H6 } from '@smui/common/elements';
    let active = 'Home';
	function setActive(value: string) {
		active = value;
	}
</script>
    
        <Item
            href="/"
            on:click={() => {
                setActive('Home');
            }}
            activated={active === 'Home'}
        >
            <Graphic class="material-icons" aria-hidden="true">home</Graphic>
            <Text>Home</Text>
        </Item>
                