---
title: Radio
description: Custom radio
category: components
file: components/FormElements/Radio
---

##### Default radio

{% example html %}

<div class="FormGroup marginBottom-0">
  <label class="Radio">
    <input class="Radio-input" name="rd-default" type="radio" />
    <span class="Radio-label">This is a custom radio with a long text to see the behaviour with multiple lines</span>
  </label>
  <label class="Radio">
    <input class="Radio-input" name="rd-default" type="radio" />
    <span class="Radio-label">This is a custom radio with a long text to see the behaviour with multiple lines</span>
  </label>
</div>

{% endexample %}

##### Disabled radio

{% example html %}

<div class="FormGroup marginBottom-0">
  <label class="Radio">
    <input class="Radio-input" disabled name="rd-disabled" type="radio" />
    <span class="Radio-label">This is a disabled radio</span>
  </label>
</div>
{% endexample %}

##### Error radio

{% example html %}

<div class="FormGroup has-error marginBottom-0">
  <label class="Radio">
    <input class="Radio-input" name="rd-error" type="radio" />
    <span class="Radio-label">This is a custom radio with error</span>
  </label>
   <label class="Radio">
    <input class="Radio-input" name="rd-error" type="radio" />
    <span class="Radio-label">This is a custom radio with error</span>
  </label>
  <p class="FormGroup-feedback">This is an error</p>
</div>
{% endexample %}

##### Multiple radios

{% example html %}

<div class="GridRow GridRow--fromMedium-2">
  <div class="GridColumn FormGroup MultipleRadio fromMedium-marginBottom-0">
    <h6>Multiple choices:</h6>
    <label class="Radio">
      <input class="Radio-input" name="rb-1" type="radio" />
      <span class="Radio-label">Javascript</span>
    </label>
    <label class="Radio">
      <input class="Radio-input" name="rb-1" type="radio" />
      <span class="Radio-label">Python</span>
    </label>
    <label class="Radio">
      <input class="Radio-input" name="rb-1" type="radio" />
      <span class="Radio-label">PHP</span>
    </label>
  </div>

  <div class="GridColumn FormGroup has-error MultipleRadio marginBottom-0">
    <h6>Select with errors:</h6>
    <label class="Radio">
      <input class="Radio-input" name="rbe-1" type="radio" />
      <span class="Radio-label">Javascript</span>
    </label>
    <label class="Radio">
      <input class="Radio-input" name="rbe-1" type="radio" />
      <span class="Radio-label">Python</span>
    </label>
    <label class="Radio">
      <input class="Radio-input" name="rbe-1" type="radio" />
      <span class="Radio-label">PHP</span>
    </label>
    <p class="FormGroup-feedback">Please select at least one option.</p>
  </div>

</div>
{% endexample %}
