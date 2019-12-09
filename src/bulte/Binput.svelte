<script>
    export let value;
    export let label;
    export let name;
    export let placeholder;
    export let color = 'is-primary';
    export let type = 'text';
    export let customClass ='';
    export let iconLeft = '';
    export let iconLeftColor = '';
    export let iconRight = '';
    export let iconRightColor = '';
    export let iconPack = 'fas';
    export let iconSize = 'is-small';
    export let help = '';
    export let expanded = false;
    export let grouped = false;
    export let groupedCenter = false;
    export let groupedRight = false;
    export let horizontal = false;
    export let loading = false;
    export let readonly = false;
    export let disabled = false;
    export let isRounded = false;
    export let isStatic = false;

    const toList = (classes) => classes.filter(v => v).join(' ');

    $: inputClass = toList([
        'input',
        customClass,
        color,
        isRounded ? 'is-rounded' : '',
        isStatic ? 'is-static' : ''
    ]);
    $: rightIconContainer = toList(['icon', iconSize, iconRightColor]);
    $: leftIconContainer = toList(['icon', iconSize, iconLeftColor]);
    $: rightIconClass = toList([iconPack, `fa-${iconRight}`]);
    $: leftIconClass = toList([iconPack, `fa-${iconLeft}`]);
    let props = {
        name: name,
        placeholder: placeholder,
        value: value,
        disabled: disabled,
        readonly: readonly
    }
</script>

<div
  class="field"
  class:is-expanded={expanded}
  class:is-grouped={grouped}
  class:is-grouped-center={groupedCenter}
  class:is-grouped-right={groupedRight}
  class:is-horizontal={horizontal}>
    {#if label}
    <label class="label">{label}</label>
    {/if}
    <div
      class="control"
      class:has-icons-left={iconLeft}
      class:has-icons-right={iconRight}
      class:is-loading={loading}>
        {#if type === "email"}
        <input class={inputClass} type="email" {...props}>
        {:else if type === "number"}
        <input class={inputClass} type="number" {...props}>
        {:else if type === "tel"}
        <input class={inputClass} type="tel" {...props}>
        {:else}
        <input class={inputClass} type="text" {...props}>
        {/if}
        {#if iconLeft}
        <span class={leftIconContainer}>
            <i class={leftIconClass}></i>
        </span>
        {/if}
        {#if iconRight}
        <span class={rightIconContainer}>
            <i class={rightIconClass}></i>
        </span>
        {/if}
    </div>
    {#if help}
    <p class="help {color}">{help}</p>
    {/if}
</div>