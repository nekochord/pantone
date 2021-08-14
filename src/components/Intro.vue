<template>
  <div id="box">
    <p id="pantone">Pantone</p>
  </div>
</template>

<style>
#box {
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

#pantone {
  font-size: 78px;
  text-align: center;
  width: inherit;
  -webkit-animation: hue 1s infinite linear;
}

@-webkit-keyframes hue {
  0% {
    color: #f35626;
  }
  50% {
    color: #feab3a;
  }
  100% {
    color: #f35626;
  }
}
</style>