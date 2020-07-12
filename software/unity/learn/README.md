# Learning Unity

-----

[Back to homepage](../../..) • [software resources guide](..) • [Unity setup guide](..)

-----

> This is just how some of us learned how to use Unity. Your use case may be different.

* [Getting Started with Unity](https://learn.unity.com/course/getting-started-with-unity) *by Unity Technologies*
  * In part 4.6, Karting Microgame: Smart Karts Training Guide, it is reccommended that you follow the text guide rather than the video guide. The video guide contains some inaccuracies and omits information that could help you create a trainable character.
  * I reccomend you skip part 4.12, Karting Microgame: Add a Ghost Driver. It is a video tutorial with no explanation included and overall an extremely unhelpful guide. Since the C# programming doesn't explain what the code does and the lady speaks so quickly that it is impossible, I've included the source code for `GhostManager.cs` in [Footnote 1](#footnote-1).

## Footnotes

### Footnote 1

Here is the source code of `GhostManager.cs`:

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public struct GhostTransform {
    public Vector3 position;
    public Quaternion rotation;
    public GhostTransform(Transform transform) {
        this.position = transform.position;
        this.rotation = transform.rotation;
    }
}

public class GhostManager : MonoBehaviour {
    public Transform kart;
    public Transform ghostKart;
    public bool recording;
    public bool playing;
    public List<GhostTransform> recordedGhostTransforms = new List<GhostTransform>();
    private GhostTransform lastRecordedGhostTransform;
    void Start() {}
    void Update() {
        if (recording == true) {
            if (kart.position != lastRecordedGhostTransform.position || kart.rotation != lastRecordedGhostTransform.rotation) {
                var = newGhostTransform = new GhostTransform(kart);
                recordedGhostTransforms.Add(newGhostTransform);
                lastRecordedGhostTransform = newGhostTransform;
            }
        }
        if (playing == true) { Play(); }
    }
    void Play() {
        ghostKart.gameObject.SetActive(true);
        StartCoroutine(StartGhost());
        playing = false;
    }
    IEnumerator StartGhost() {
        for (int i = 0; i < recordedGhostTransforms.Count; i++) {
            ghostKart.position = recordedGhostTransforms[i].position;
            ghostKart.rotation = recordedGhostTransforms[i].rotation;
            yield return new WaitForFixedUpdate();
        }
    }
}

```
