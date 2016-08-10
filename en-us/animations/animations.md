---
permalink: /en-US/animations/animations.htm
title: UWP Community toolkit Animations 
description: Animations allow you to implement specific XAML behaviors and apply visual composition to your application, such as Blur and Fade. You can also use code to chain animations together without using XAML.
keywords: windows, app, toolkit, animation behavior, XAML behavior, animation, composition 
layout: default
search.product: eADQiWindows 10XVcnh
---

# Animations

UWP Community toolkit provides several tools to animate your UIElements.
You can decide to use behaviors and for isntance setup your animations using Blend or you can decide to do it manually using code.

You can find individual documentation here:
* [Blur](blur.htm)
* [Fade](fade.htm)
* [Offset](offset.htm)
* [Parallax](parallax.htm)
* [Rotate](rotate.htm)
* [Scale](scale.htm)

## Behaviors
Behaviors are powerful tools for designers that can be defined in Blend:

```xaml

    <interactivity:Interaction.Behaviors>
        <behaviors:Blur x:Name="BlurBehavior" 
           Value="10" 
           Duration="10" 
           Delay="0" 
           AutomaticallyStart="True"/>
    </interactivity:Interaction.Behaviors>

```

You can specify to start animation automatically upon loading (with `AutomaticallyStart="True") or you can use code to do it manually.

## Animations using code only
For developers, the toolkit provides extensions for UIElement to match what can be done with behaviors.

So for instance if you want to blur an element, you only need to call this code:

```C#
await ToolkitLogo.Blur(duration: 10, delay: 0, value: 10).StartAsync();       
```
### Async/await
Animations are asynchronous by essence.

You can then await an animation if you start it with `StartAsync()` but there is also a non-awaitable (but still asynchronous) version if you start it with `Start()`:
```C#
await ToolkitLogo.Blur(duration: 10, delay: 0, value: 10).StartAsync();       
ToolkitLogo.Blur(duration: 10, delay: 0, value: 10).Start();
```

### Chaining animations
You can also chain animations thanks to the toolkit fluid API:

```C#
await element.Rotate(value: 30f).Fade(value: 0.5).Blur(value: 2).StartAsync();
```

In this case the toolkit will trigger a rotation, a fade and a blur simultaneously.

If you want to start animations in a serial way, you can use `Then()`:
```C#
await element.Rotate(value: 30f).Then().Fade(value: 0.5).Then().Blur(value: 2).StartAsync();
```

Every animation can have its own duration but there is a way to set it up for all animations at once:

```C#
    var anim = element.Rotate(value: 30f).Fade(value: 0.5).Blur(value: 5);
    anim.SetDurationForAll(2);
    anim.StartAsync();
```

As animations are awaitable, it is easy to execute code after animations are completed.
If you do not want to await your animations, you can then use the Completed event:

```C#
    var anim = element.Rotate(value: 30f).Fade(value: 0.5).Blur(value: 5);

    anim.Completed += animation_completed;

    anim.Start();
```

And if you want to stop an animation before it ends, jsut call `Stop()`:
```C#
    var anim = element.Rotate(value: 30f).Fade(value: 0.5).Blur(value: 5);
    anim.Start();

    anim.Stop();
```

## How does it work under the hood?

Animations can be done using XAML storyboards or Windows Composition.
By default the toolkit will use XAML storyboards unless you set `AnimationSet.UseComposition = true`.

### Using Windows Composition

While Windows Composition is faster and more efficient than XAML storyboards, it is important to understand several drawbacks that you may face when using it.

If you are using SDK 10586, Windows Composition and XAML storyboards behave exactly in the same way.

If you are using SDK 14393, the interoperabilty between XAML and Windows Composition changed (as stated by this [article](https://github.com/Microsoft/WindowsUIDevLabs/wiki/XAML-Composition-Interop-Behavior-Changes)).
In a nutshell, animating Offset and opacity with Windows Composition is only recommended if you do not change these states on XAML side. 
If you want to use Windows Composition and animate offset, then the safest way is to use a layout in XAML which positions the element at 0,0.
same for opacity where it is recommended to not define it in XAML.


### Offset, Scale and rotate
When using storyboards for offset, scale and rotate, the toolkit will generate a CompositeTransform for you and will merge it with the current UIElement.RenderTransform (using a TransformGroup).
This means that you do not have to worry about the current state of your UIElement because the toolkit will take care of keeping it unchanged.