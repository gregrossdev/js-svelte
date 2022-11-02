<script>
    import TextInputs from './text-inputs.svelte'
    import NumericInputs from './numeric-inputs.svelte'
    import CheckboxInputs from './checkbox-inputs.svelte'
    import GroupInputs from './group-inputs.svelte'
    import TextareaInputs from './textarea-inputs.svelte'
    import SelectBindings from './select-bindings.svelte'
    import SelectMultiple from './select-multiple.svelte'
    import ContentEditable from './contenteditable-bindings.svelte'
    import EachBlockBindings from './each-block-bindings.svelte'
    import MediaElements from './media-elements.svelte'
    import Dimensions from './dimensions.svelte'
    import This from './this.svelte'
    import Keypad from './keypad.svelte'
    import InputField from './binding-component-instances.svelte'

    let pin;
    $: view = pin ? pin.replace(/\d(?!$)/g, '•') : 'enter your pin';

    function handleSubmit() {
        alert(`submitted ${pin}`);
    }

    let field;
</script>

<section>
    <TextInputs/>
    <NumericInputs/>
    <CheckboxInputs/>
    <GroupInputs/>
    <TextareaInputs/>
    <SelectBindings />
    <SelectMultiple />
    <ContentEditable />
    <EachBlockBindings />
    <MediaElements />
    <Dimensions />
    <This />
    <h3>Keypad</h3>
    <h4 style="color: {pin ? '#333' : '#ccc'}">{view}</h4>
    <Keypad bind:value={pin} on:submit={handleSubmit}/>
    <h3>Binding to Component Instances</h3>
    <InputField bind:this={field}/>
    <button on:click={() => field.focus()}>Focus field</button>
</section>
