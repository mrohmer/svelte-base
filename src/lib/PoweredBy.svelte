<script lang='ts'>
	export let technologies: string[] = ['svelte'];
	export let name: string;
	export let url: string;
	export let sourceCodeUrl: string;
	export let sourceCodePlatform = 'Github';

	$: technologiesStr = [[...technologies].splice(0, technologies.length - 1).join(', '), technologies[technologies.length - 1]].filter(i => !!i).join(' & ');
</script>

<style lang='scss'>
  .powered-by {
    font-size: 12px;
    text-align: center;
    padding: 10px;

    margin-top: 50px;

    &__heart {
      color: red;
    }

    a {
      text-decoration: none;

      &:hover {
        text-decoration: underline;
      }
    }
  }
</style>
<div class='powered-by'>
	Made with <span class="powered-by__heart">♥️</span>
	{#if technologies.length > 1}
		, {[...technologies].splice(0, technologies.length - 1).join(', ')}
	{/if}
	{#if technologies.length > 0}
		& {technologies[technologies.length - 1]}
	{/if}
	{#if name && url}
		by <a href={url}>{name}</a>.
	{:else if name }
		by {name}.
	{/if}
	{#if sourceCodeUrl}
		<br>
		View the source code on <a href={sourceCodeUrl}>{sourceCodePlatform}</a>.
	{/if}
</div>
