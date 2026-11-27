---
name: threejs-animation
description: Build or change animated 3D scenes using Three.js. Use for loading glTF or GLB, choosing procedural or clip-based motion, controlling playback, and integrating animation with the scene lifecycle.
---

### Find the scene owner

Check the installed `three` version, the nearest working scene, and the project's public 3D API. The example below uses the r187 library API. In an application with a framework wrapper, use the wrapper's entry points and implement missing Three.js behavior in the package that owns the scene.

Identify the renderer and canvas, the scene graph, the active camera, the frame callback, and their owner. For an existing viewer, attach the model to its scene and register updates in its frame loop. For a standalone viewer, initialize the renderer once, size it to its container, update the camera projection on resize, and render the scene with that camera after applying frame updates.

### Choose what drives the motion

- For a spin or bob defined by code, use elapsed time or a rate multiplied by delta seconds. Apply transforms to the intended object or parent group.
- For an authored animation, inspect `gltf.animations` for the actual clip names, durations, and tracks. An `AnimationClip` stores the keyframes, an `AnimationMixer` applies them to a model hierarchy, and an `AnimationAction` controls playback of one clip. Give independently animated instances their own playback state. Let a single mechanism drive each animated property.
- An asset with no clips can still be a valid static model. If the feature requires a clip, surface the missing asset capability. Check that skeletal and morph tracks bind to nodes beneath the mixer's root when a playing action produces no visible motion.

### Play and switch clips

Here `scene` belongs to the viewer, `assetUrl` is the configured model URL, and this example asset supplies two named clips. Using the library directly:

```js
import { AnimationClip, AnimationMixer } from 'three';
import { GLTFLoader } from 'three/addons/loaders/GLTFLoader.js';

const gltf = await new GLTFLoader().loadAsync(assetUrl);
const model = gltf.scene;
const idleClip = AnimationClip.findByName(gltf.animations, 'Idle');
const walkClip = AnimationClip.findByName(gltf.animations, 'Walk');
if (!idleClip || !walkClip) {
  throw new Error('The character asset must provide Idle and Walk clips');
}

scene.add(model);
const mixer = new AnimationMixer(model);
const idle = mixer.clipAction(idleClip).play();
const walk = mixer.clipAction(walkClip);

function startWalking() {
  walk.reset().play();
  idle.crossFadeTo(walk, 0.25, false);
}
```

In the viewer's existing frame callback, call `mixer.update(deltaSeconds)` once before rendering. Use the viewer's timing source. When consuming raw frame timestamps, convert the difference from milliseconds to seconds. Invoke `startWalking()` on the transition into walking; calling it on each frame restarts the incoming clip. For one-shot actions, set the action's loop mode to `LoopOnce`; choose `clampWhenFinished` when the final pose should remain visible.

### Release and verify

When replacing the model or unmounting the viewer, detach its frame callback, stop its actions, call `mixer.uncacheRoot(model)` for this dedicated mixer, and remove the model from the scene. Dispose of geometries, materials, textures, controls, and renderers according to ownership; shared or cached assets remain available to other viewers.

In the actual viewer, play one clip, switch to the second, then reopen the scene. Check the animated pose or track value changing, the intended transition, and that remounting leaves one active update per instance.

[Three.js r187 animation source](https://github.com/mrdoob/three.js/tree/r187/src/animation) · [Three.js r187 glTF loader](https://github.com/mrdoob/three.js/blob/r187/examples/jsm/loaders/GLTFLoader.js) · [Related community skill](https://github.com/CloudAI-X/threejs-skills/blob/main/skills/threejs-animation/SKILL.md)
