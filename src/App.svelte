<script lang="ts">
let sliderValue = 50;
let tiltValue = 0;

function get_gravity_value(tilt) {
  let grow = (tilt**3)/200;
  return grow;
}

setInterval(() => {
  sliderValue = sliderValue + get_gravity_value(tiltValue);
  if (sliderValue >=100) {
    sliderValue = 100;
  } else if (sliderValue <= 0) {
    sliderValue = 0;
  }
  console.log(sliderValue);
}, 50);

</script>

<main>
  <div class="slidergraivity">
    <div class="slidecontainer">
      <h1>Dumb volume selector</h1>
      <input bind:value={sliderValue} type="range" min="0" max="100" class="slider" id="myRange" style="transform: rotate({tiltValue}deg)" disabled={true} >
      <label for="myRange" class="value">{Math.round(sliderValue)}</label>
      <div class="tiltselector">
        <input class="button" type="button" value="+" on:click={() => tiltValue += 3}>
        <input class="button" type="button" value="-" on:click={() => tiltValue -= 3}>
      </div>
    </div>
  </div>
</main>


<style>
  div.slidergraivity {
    display: flex;
    justify-content: center;
  }
  div h1 {
    justify-content: center;
    font-size: 3rem;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  }

  div.slidecontainer {
    /* width: 100%; */
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  div.slidecontainer input.slider {
    width: 400px;
    height: 400px;
  }
  div.slidecontainer input.button{
    width: 50px;
    height: 50px;
    border-radius: 50%;
    background-color: #f1f1f1;
    border: none;
    text-align: center;
    font-size: 30px;
    margin: 0 auto;
    cursor: pointer;
    outline: none;

  }

  div.slidecontainer label {
    display: flex;
    justify-content: center;
    font-size: 2rem;
    font-family: fantasy;
  }

</style>