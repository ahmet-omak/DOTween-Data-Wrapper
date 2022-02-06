# DOTween-Data-Wrapper



## Table Of Contents 
 
<details>
<summary>Details</summary>

  - [Introduction](#introduction)
  - [Normal DOTween Usage](#normal-dotween-usage)
  - [DOTween Data Wrapper Usage 1](#ddw-dotween-usage)
  - [DOTween Data Wrapper Usage 2](#ddw-other-dotween-usage)
  - [Components](#components)
     - [Transform](#transform)
  - [Examples](#examples)
    
</details>

## Introduction
A component-based DOTween data wrapper (DDW), built specifically to make life easier for developers.

    
## Normal DOTween Usage
    
```csharp
    using UnityEngine;
    using DG.Tweening;
 
    public class DOTweenGenericWay : MonoBehaviour
    {
        private Tween tween;

        private void Start()
        {
            tween = transform.DOMoveX(5f, 1f)
                .SetDelay(.2f)
                .SetEase(Ease.OutSine)
                .SetAutoKill(true)
                .SetRecyclable(true)
                .Play();
        }
    }
```
 - The example above shows how to do tweening using one of the DOTween's functions. Even though DOTween is a great tweening library, I believe I can make it much more 
 easier for the developers.
 
 ## DDW DOTween Usage
 
   #### Recommended Way
 
 ```csharp
    using UnityEngine;
    using DG.Tweening;
 
    public class DDWSolution : MonoBehaviour
    {
        public BaseTweenData baseTweenData;

        private Tween tween;

        private void Start()
        {
            tween = baseTweenData.GetTween(gameObject).Play();
        }
    }
```
 - With the DDW (DOTween Data Wrapper), you don't need to know your tween type (MoveTween, RotateTween, ScaleTween, etc.). You just need a "BaseTweenData" object to get the data you need in order to do tweening. At this moment, you migth ask a question "How in the earth would it know what tween type I want it to tween?". It is simple indeed. 
You tell it how to tween in the editor like below.

<img src = "Assets/Images/example_1.png" >

Note the following
 - In order to use GetTween function, you need to pass in a gameObject. There is also a way where you don't need to pass in any argument.

## DDW Other DOTween Usage

   #### Not Recommended Way

 ```csharp
    using UnityEngine;
    using DG.Tweening;
    
    public class TestCubeController : BaseTestController
    {
        public MoveTweenData tweenData;

        private Tween tween;

        private void Start()
        {
            tween = transform.DOMove(tweenData.EndValue, tweenData.Duration)
                .SetDelay(.2f)
                .SetEase(Ease.OutSine)
                .SetAutoKill(true)
                .SetRecyclable(true)
                .Play();
        }
}
```
If you don't feel confident with the gameObject you have to pass in, you might want to use DDW as shown above. Note that, In order to use DDW like that, you need a
"XXXTwenData" object (in this case, it's MoveTweenData) not a BaseTweenData. You also make sure that you no longer will change the tween data in the editor with a different
tween data anymore such as ScaleTweenData,RotateTweenData, etc.

## Components

Supports the following components

- Transform
- Mesh Renderer (In Progress)

### Transform
Supports the following DOTween's functions

1 - Move Tween
  - DOMove
  - DOMoveX/DOMoveY/DOMoveZ
  - DOLocalMove
  - DOLocalMoveX/DOLocalMoveY/DOLocalMoveZ

2 -  Rotate Tween
   - DORotate
   - DOLocalRotate
   - DORotateQuaternion
   - DOLocalRotateQuaternion

3 - Scale Tween
   - DOScale
   - DOScaleX/DOScaleY/DOScaleZ

## Examples

## Example 1

https://user-images.githubusercontent.com/59537269/152651000-75c808cc-7fac-424c-bc0f-a170fa732d9f.mp4

## Example 2

https://user-images.githubusercontent.com/59537269/152651221-dc2a996a-721b-43d8-baeb-7a3ce902b712.mp4


