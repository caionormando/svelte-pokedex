<div class="header-container">
  <div class="circles-container">
    <div class="blue-circle" />
    <div class="secondary-circles">
      <div class="red-circle" />
      <div class="yellow-circle" />
      <div class="green-circle" />
    </div>
  </div>
  <div class="diagonal-container">
    <div class="diagonal-line" />
  </div>
  <div class="line-container" />
  <img src="images/pokemon_title.png" alt="Pokémon Title" />
</div>

<style>
  .header-container {
    display: flex;
    height: 100%;
    width: 100%;
  }

  .circles-container {
    position: relative;
    width: 25%;
    border-bottom: solid 3px;
  }

  .circles-container > div {
    position: absolute;
  }

  .blue-circle {
    height: 75%;
    width: 30%;
    background-image: linear-gradient(to right, white, #34aada);
    border: solid 3px darkgray;
  }

  .secondary-circles {
    position: absolute;
    display: flex;
    justify-content: space-between;
    width: 35%;
    height: 100%;
    left: 80px;
  }

  .blue-circle,
  .secondary-circles > div {
    border-radius: 50%;
  }

  .secondary-circles > div {
    height: 25%;
    width: 20%;
    top: -1px;
  }

  .secondary-circles .red-circle {
    background-image: linear-gradient(to bottom right, white, #ff3434);
    border: solid 1px darkgray;
  }

  .secondary-circles .yellow-circle {
    background-image: linear-gradient(to bottom right, white, #edb825);
    border: solid 1px darkgray;
  }

  .secondary-circles .green-circle {
    background-image: linear-gradient(to bottom right, white, #16822d);
    border: solid 1px darkgray;
  }

  .header-container .line-container,
  .header-container .circles-container {
    width: 42.5%;
  }

  .diagonal-container {
    position: relative;
    width: 15%;
  }

  .diagonal-container .diagonal-line {
    width: 135%;
    height: 100%;
    border-bottom: 3px solid;
    -webkit-transform: translateY(20px) translateX(5px) rotate(-44deg);
    position: absolute;
    top: -39px;
    left: -32px;
  }

  .header-container .line-container {
    height: 0%;
    border-bottom: solid 3px;
  }

  .header-container img {
    position: absolute;
    width: 30%;
    left: 215px;
    top: 15px;
  }
  /* ##################################################################DESKTOP VERSION############################################################################################## */

  @media (min-width: 768px) {
    .blue-circle {
      height: 80%;
      width: 25%;
	  top: 5px;
	  left: 30px;
    }

    .red-circle {
      height: 10%;
      width: 5%;
      left: 195px;
      top: 8px;
    }

    .yellow-circle {
      height: 10%;
      width: 5%;
      left: 195px;
      top: 8px;
    }

    .green-circle {
      height: 10%;
      width: 5%;
      left: 195px;
      top: 8px;
    }

    .diagonal-container .diagonal-line {
      width: 110%;
      -webkit-transform: translateY(20px) translateX(5px) rotate(-24deg);
      top: -78px;
      left: -62px;
    }

    .header-container .line-container {
      height: 38%;
    }

    .header-container img {
      width: 20%;
      left: 1245px;
      top: 93px;
    }

    .secondary-circles {
      left: 435px;
    }
  }
</style>
