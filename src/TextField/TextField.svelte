<script lang="ts">
  import Field from "../Field";
  import type { Status } from "../Field/Field.svelte";
  import createId from "../utils/createId";

  export let label = "";
  export let id = createId();
  export let message = "";
  export let skeleton = false;
  export let status: Status = "default";
  export let gutter = false;
  export let value = "";
  export let rootClass = "";
  export let fieldRef: HTMLDivElement = null;
  export let ref: HTMLInputElement = null;
</script>

<Field
  class={rootClass}
  bind:ref={fieldRef}
  bind:label
  bind:status
  bind:id
  bind:message
  bind:skeleton
  bind:gutter>
  <span slot="before">
    <slot name="before" />
  </span>
  <input
    {...$$restProps}
    bind:this={ref}
    bind:value
    on:change
    on:blur
    on:focus
    {id} />
  <span slot="after">
    <slot name="after" />
  </span>
</Field>
