<script lang="ts">
import Fa from 'svelte-fa';
import { faExclamationCircle } from '@fortawesome/free-solid-svg-icons';
import Tooltip from './Tooltip.svelte';

export let error: string;
export let icon = false;
</script>

{#if icon}
  {#if error !== undefined && error !== ''}
    <Tooltip top>
      <svelte:fragment slot="content">
        <Fa size="1.125x" class="cursor-pointer text-red-500 {$$props.class}" icon="{faExclamationCircle}" />
      </svelte:fragment>
      <svelte:fragment slot="tip">
        {#if error}
          <div class="inline-block py-2 px-4 rounded-md bg-charcoal-800 text-xs" aria-label="tooltip">{error}</div>
        {/if}
      </svelte:fragment>
    </Tooltip>
  {/if}
{:else}
  <div
    class="text-red-500 p-1 flex flex-row items-center {$$props.class}"
    class:opacity-0="{error === undefined || error === ''}">
    <Fa size="1.125x" class="cursor-pointer text-red-500" icon="{faExclamationCircle}" />
    <div role="alert" aria-label="Error Message Content" class="ml-2">{error}</div>
  </div>
{/if}
