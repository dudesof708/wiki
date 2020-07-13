# Learning Unity

-----

[Back to homepage](../../..) • [software resources guide](..) • [Unity setup guide](..)

-----

> This is just how some of us learned how to use Unity. Your use case may be different.

* [Essential Unity Concepts](https://learn.unity.com/tutorial/essential-unity-concepts) *by Unity Technologies*
* [Getting Started with Unity](https://learn.unity.com/course/getting-started-with-unity) *by Unity Technologies*
  * This guide is pretty helpful to learning where all the buttons in Unity are. You don't have to do the whole tutorial to get the hang of it, but I do reccomend skipping over the 3D projects and just doing the 2D project if you're interested in saving time. I did the whole thing.
  * In part 4.6, Karting Microgame: Smart Karts Training Guide, it is reccommended that you follow the text guide rather than the video guide. The video guide contains some inaccuracies and omits information that could help you create a trainable character.
  * I reccomend you skip part 4.12, Karting Microgame: Add a Ghost Driver. It is a video tutorial with no explanation included and overall an extremely unhelpful guide. Since the C# programming doesn't explain what the code does and the lady speaks so quickly that it is impossible, I've included the source code for `GhostManager.cs` in [Footnote 1](#footnote-1).
  * For part 4.18, Karting Microgame: Build Your Own Track, the project requires a plugin called **ProGrids**. This doesn't come installed by default, so see [Footnote 2](#footnote-2) on how to install it.
* [Beginning 2D Game Development](https://learn.unity.com/course/beginning-2d-game-development) *by Unity Technologies*
* [How to make a 2D Platformer](https://www.youtube.com/playlist?list=PLPV2KyIb3jR42oVBU6K2DIL6Y22Ry9J1c) *by Brackeys*

## FAQ

**I'm getting a Unity package manager error with options Retry, Quit, and Continue!** It mentions editing my `package.json` file and an error while resolving packages.

> This is an internet connection issue with Unity's analytics package. Go to your project folder's Packages folder, and open `package.json`. Inside, find the line that says `com.unity.analytics` and delete it. Restart Unity, and you should be able to open the project now.

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

### Footnote 2

Here's how to install **ProGrids**, a plugin for Unity:

1. From the toolbar, open **Window > Package Manager**.
2. Search for **ProGrids**.
   ![ProGrids](https://i.imgur.com/3x0RPe6.png)
3. Click **Install** in the bottom right corner.
