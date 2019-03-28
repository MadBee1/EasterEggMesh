var scene = new THREE.Scene();
var camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 );

var renderer = new THREE.WebGLRenderer();
renderer.setSize( window.innerWidth, window.innerHeight );
document.body.appendChild( renderer.domElement ); 
window.addEventListener('resize', () => {
  renderer.setSize(window.innerWidth, window.innerHeight);
  camera.aspect = window.innerWidth / window.innerHeight;
  
  camera.updateProjectMatrix();
})

// The code from StackOverflow (edited)
var points = [];
for ( var deg = 0; deg <= 180; deg += 1 ) {

    var rad = Math.PI * deg / 180;
    var point = new THREE.Vector2( ( 0.72 + .08 * Math.cos( rad ) ) * Math.sin( rad ), - Math.cos( rad ) ); // the "egg equation"
    //console.log( point ); // x-coord should be greater than zero to avoid degenerate triangles; it is not in this formula.
    points.push( point );

}

geometry = new THREE.LatheBufferGeometry( points, 64 );
var material = new THREE.MeshPhongMaterial( { color: 0xFFDCC4, shading: THREE.FlatShading } ); // Material.
var egg = new THREE.Mesh( geometry, material ); // Mesh.
scene.add( egg );
camera.position.z = 4;

var directionalLight = new THREE.DirectionalLight( 0xffffff, 0.5 );
directionalLight.position.set( 0, 1, 0 );
scene.add( directionalLight );

var light = new THREE.AmbientLight( 0x404040 ); // Soft light.
scene.add( light );

function render() {
  requestAnimationFrame( render );
  egg.rotation.y += 0.007;

  renderer.render( scene, camera );
}
 render();
