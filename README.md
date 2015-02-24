three.js
========
#### What this branch is about? ####

This branch of the three.js includes changes and a new Canvas3DRenderer that allows it to run inside the QtQuick JavaScript environment and use the QtCanvas3D module for rendering. See https://qt.gitorious.org/qt/qtcanvas3d 

The ready built libraries are meant to be used with Qt 5.4.1 and the Canvas3D Technology Preview 2. To build three.js that works with Qt 5.5 dev branch you need to use the utils/build/build_qt_5_5.sh script to build a new library that drops the unneeded TypedArray wrappers and includes the correct version of Canvas3DRenderer for Qt 5.5 that matches the new API.

#### JavaScript 3D library ####

The aim of the project is to create a lightweight 3D library with a very low level of complexity — in other words, for dummies. The library provides &lt;canvas&gt;, &lt;svg&gt;, CSS3D, WebGL and Qt Canvas3D renderers.

[Examples](http://threejs.org/) — [Documentation](http://threejs.org/docs/) — [Migrating](https://github.com/mrdoob/three.js/wiki/Migration) — [Help](http://stackoverflow.com/questions/tagged/three.js)


### Usage ###

Download the [minified library](http://threejs.org/build/three.min.js) and include it in your html.
Alternatively see [how to build the library yourself](https://github.com/mrdoob/three.js/wiki/build.py,-or-how-to-generate-a-compressed-Three.js-file).

```html
<script src="js/three.min.js"></script>
```

This code creates a scene, then creates a camera, adds the camera and cube to the scene, creates a &lt;canvas&gt; renderer and adds its viewport in the document.body element.

```html
<script>

	var camera, scene, renderer;
	var geometry, material, mesh;

	init();
	animate();

	function init() {

		camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 1, 10000 );
		camera.position.z = 1000;

		scene = new THREE.Scene();

		geometry = new THREE.BoxGeometry( 200, 200, 200 );
		material = new THREE.MeshBasicMaterial( { color: 0xff0000, wireframe: true } );

		mesh = new THREE.Mesh( geometry, material );
		scene.add( mesh );

		renderer = new THREE.CanvasRenderer();
		renderer.setSize( window.innerWidth, window.innerHeight );

		document.body.appendChild( renderer.domElement );

	}

	function animate() {

		// note: three.js includes requestAnimationFrame shim
		requestAnimationFrame( animate );

		mesh.rotation.x += 0.01;
		mesh.rotation.y += 0.02;

		renderer.render( scene, camera );

	}

</script>
```
If everything went well you should see [this](http://jsfiddle.net/Gy4w7/).

### Change log ###

[releases](https://github.com/mrdoob/three.js/releases)
