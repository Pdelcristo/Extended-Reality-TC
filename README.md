!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Object World</title>
  <meta name="description" content="A rich, interactive VR scene with A-Frame">
  <script src="https://aframe.io/releases/1.4.2/aframe.min.js"></script>
  <script src="https://unpkg.com/aframe-physics-system@1.4.0/dist/aframe-physics-system.min.js"></script>
  <script src="https://unpkg.com/aframe-extras@6.1.1/dist/aframe-extras.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/aframe-environment-component/dist/aframe-environment-component.min.js"></script>
</head>
<body>
  <a-scene
    physics="gravity: -9.8"
    shadow="type: pcfsoft"
    fog="type: exponential; color: #AAA; density: 0.05"
    environment="preset: forest; ground: flat; lighting: distant"
  >

    <!-- Assets -->
    <a-assets>
      <img id="skyTexture" src="https://cdn.aframe.io/360-image-gallery-boilerplate/img/sechelt.jpg">
      <img id="groundTexture" src="https://cdn.aframe.io/a-painter/images/floor.jpg">
      <a-asset-item id="treeModel" src="https://cdn.aframe.io/test-models/models/tree/scene.gltf"></a-asset-item>
    </a-assets>

    <!-- Animated Sky -->
    <a-sky src="#skyTexture" rotation="0 0 0"
           animation="property: rotation; to: 0 360 0; loop: true; dur: 60000"></a-sky>

    <!-- Lighting -->
    <a-light type="ambient" color="#ffffff" intensity="0.4"></a-light>
    <a-light type="directional" position="3 5 2" intensity="1" castShadow></a-light>

    <!-- Ground -->
    <a-plane src="#groundTexture" rotation="-90 0 0" width="100" height="100"
             shadow="receive: true" repeat="30 30" static-body></a-plane>

    <!-- Objects -->
    <a-box position="-2 4 -5" rotation="0 45 0" color="#4CC3D9" dynamic-body shadow
           animation__hover="property: scale; to: 1.5 1.5 1.5; startEvents: mouseenter"
           animation__leave="property: scale; to: 1 1 1; startEvents: mouseleave">
    </a-box>

    <a-sphere position="0 3 -5" radius="1.25" color="#EF2D5E" shadow
              animation="property: position; dir: alternate; dur: 2000; loop: true; to: 0 4 -5">
    </a-sphere>

    <a-cylinder position="2 1.25 -5" radius="0.5" height="2.5" color="#FFC65D" shadow></a-cylinder>

    <!-- 3D Model -->
    <a-entity gltf-model="#treeModel" position="4 0 -6" scale="0.5 0.5 0.5" shadow></a-entity>

    <!-- Teleportation / Movement Controls -->
    <a-entity id="rig" movement-controls position="0 1.6 0">
      <a-entity camera look-controls wasd-controls>
        <a-cursor color="red" fuse="true" timeout="500"></a-cursor>
      </a-entity>
    </a-entity>

    <!-- Text -->
    <a-entity text="value: Welcome to Object World!; color: white; width: 6"
              position="-3 5 -7" scale="1.5 1.5 1.5">
    </a-entity>

  </a-scene>
</body>
</html>
