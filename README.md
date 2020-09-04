# Unity Editor Toolbox

## Introduction

Improve usability and clarity of key features in Unity Editor for better workflow!

This Toolbox not only extends functionalities, it does so with the user in mind.
Written to be as flexible and optimized as possible. Now you and other programming professionals will be able to create a readable and useful component editor simply by using attributes. You’ll get fast and clear access to data from Game Objects placed in the Scene. Lastly, you’ll gain more control over the Project Window. Go ahead, customize those folder icons.

It's worth to mention that prepared drawers are based on the custom, layout-based system. Additionally, I’m leaving you some useful scripts, classes, and functions that facilitate Editor extensions development.

Learn all the details about the main features below.

## System Requirements
Unity 2018.x or newer
 
## Installation

- Install Editor Toolbox package:
	- 1 way: Find Unity Package Manager (Window/Package Manager) and add package using this git URL:
	```
	https://github.com/arimger/Unity-Editor-Toolbox.git#upm
	```
	- 2 way: Copy and paste `Editor Toolbox` directory into your project (Assets/...)
- Open Edit/Project Settings/Editor Toolbox window
- If Toolbox Editor Settings is not available, press "Try to find the settings file" button or create new
- Manage settings in your way
	- Enable/disable Hierarchy overlay, choose allowed information
	- Enable/disable Project icons or/and assign own directories
	- Enable/disable Toolbox drawers or/and assign custom drawers

## Table Of Contents

- [Attributes&Drawers](#drawers)
	- [Regular Drawers](#regulardrawers)
	- [Toolbox Drawers](#toolboxdrawers)
- [Reorderable List](#reorderable-list)
- [Editor Extensions](#editor-extensions)
	- [Hierarchy](#hierarchy)
	- [Project](#project)
	- [Toolbar](#toolbar)
- [Editor Extras](#editor-extras)

## Settings

The most important file, it allows the user to manage all available features. Can be accessed from the Project Settings window (Edit/Project Settings.../Editor Toolbox) or directly inside the Project window. Make sure to have one valid settings file per project.

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/doc14.png)

Available features are divided into three groups:
- Hierarchy
- Project
- Inspector/Drawers

Each module is described in its respective section.

## Attributes&Drawers <a name="drawers"></a>

### Regular Drawers <a name="regulardrawers"></a>

Drawers based on build-in classes **PropertyDrawer/DecoratorDrawer** and associated **PropertyAttribute**.

&nbsp;

> Editor Toolbox/Scripts/Attributes/\
> Editor Toolbox/Editor/Drawers/

&nbsp;

#### HelpAttribute

```csharp
[Help("You can provide more information in HelpBoxes.", order = 100)]
public int var1;
```

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc1.png)

#### TagSelectorAttribute

```csharp
[TagSelector]
public string var1;
```

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc2.png)

#### SeparatorAttribute

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc3.png)

#### ProgressBarAttribute

```csharp
[ProgressBar(minValue:0.0f, maxValue:100.0f)]
public float var1 = 36.0f;
```

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc4.png)
![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc5.png)

#### NewLabelAttribute

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc12.png)

#### MinMaxSliderAttribute

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc6.png)

#### IndentAttribute

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc7.png)

#### ConditionalShowAttribute & ConditionalHideAttribute

```csharp
public bool toggle;
[ConditionalShow(nameof(toggle), true)]
public float var1;
```

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc9.png)
![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc8.png)

#### ConditionalEnableAttribute & ConditionalDisableAttribute

```csharp
public bool toggle;
[ConditionalEnable(nameof(toggle), true)]
public float var1;
```

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc24.png)
![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc25.png)

#### AssetPreviewAttribute

```csharp
[AssetPreview]
public GameObject var1;
```

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc10.png)

#### HideLabelAttribute

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc11.png)

#### SuffixAttribute

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc13.png)

#### TypeConstraintAttribute

```csharp
[ClassExtends(typeof(UnityEngine.Object))]
public SerializedType type1;
[ClassImplements(typeof(System.Collections.ICollection))]
public SerializedType type2;
```

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc14.png)

#### ReadOnlyFieldAttribute

```csharp
[ReadOnlyField]
public int var1;
```

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc15.png)

#### EnumFlagAttribute

```csharp
[System.Flags]
public enum FlagExample
{
    Nothing = 0,
    Flag1 = 1,
    Flag2 = 2,
    Flag3 = 4,
    Everything = ~0
}

[EnumFlag]
public FlagExample enumFlag = FlagExample.Flag1 | FlagExample.Flag2;
```

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc20.png)

```csharp
[EnumFlag(EnumStyle.Button)]
public FlagExample enumFlag = FlagExample.Flag1 | FlagExample.Flag2 | FlagExample.Flag4 | FlagExample.Flag8;
```

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc35.png)

#### NotNullAttribute

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc21.png)
![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc22.png)

#### RandomAttribute

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc23.png)

#### DirectoryAttribute

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc26.png)
![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc27.png)

#### BroadcastButtonAttribute

```csharp
//NOTE1: to broadcast messages in Edit mode desired component has to have [ExecuteAlways] or [ExecuteInEditMode] attribute
//NOTE2: Unity broadcasting will invoke all matching methods on this behaviour

[BroadcastButton(nameof(MyMethod), "Click me to broadcast message", ButtonActivityType.OnEditMode, order = 100)]
public int var1;

private void MyMethod()
{
	Debug.Log("MyMethod is invoked");
}
```

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc28.png)

#### InstanceButtonAttribute

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc29.png)

#### SceneNameAttribute

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc30.png)
![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc31.png)

#### PresetAttribute

```csharp
private readonly int[] presetValues = new[] { 1, 2, 3, 4, 5 };

[Preset(nameof(presetValues))]
public int presetTarget;
```

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc33.png)

#### SearchableEnumAttribute

```csharp
[SearchableEnum]
public KeyCode enumSearch;
```

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc34.png)

#### ClampAttribute

```csharp
[Clamp(minValue = 1.5f, maxValue = 11.3f)]
public double var1;
```

#### Vector2DirectionAttribute & Vector3DirectionAttribute

```csharp
[Vector2Direction]
public Vector2 direction2d;
[Vector3Direction]
public Vector3 direction3d;
```

#### PasswordAttribute

```csharp
[Password]
public string password;
```
---

### Toolbox Drawers <a name="toolboxdrawers"></a>

Drawers are based on classes inherited from the **ToolboxDrawer** class and associated **ToolboxAttribute**. With this powerful custom system you are able to create really flexible drawers. You can use them without limitations (they work with sub-classes and as array children). Every ToolboxDrawer is layout-based. For proper work they need at least one settings file located in your project. You can find predefined one here - `Editor Toolbox/EditorSettings.asset`.

&nbsp;

> Editor Toolbox/Scripts/Attributes/ToolboxAttributes\
> Editor Toolbox/Editor/Drawers/ToolboxDrawers

&nbsp;

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/doc5.png)

#### ToolboxDecoratorAttributes

Display/create something before and after property in the desired order (using Order property).   
In fact **ToolboxDecoratorDrawers** are like extended version of built-in **DecoratorDrawers**. 
Unfortunately, standard decorators won't always work with ToolboxDrawers so try to use this replacement instead.

```csharp
[BeginGroup("Group1")]
public int var1;
public int var2;
public int var3;
[EndGroup]
public int var4;
```
```csharp
[BeginHorizontal]
public int var1;
public int var2;
[EndHorizontal]
public int var3;
```
```csharp
[BeginIndent]
public int var1;
public int var2;
public int var3;
[EndIndent]
public int var4;
```
```csharp
[SpaceArea(spaceBefore = 10.0f, spaceAfter = 5.0f, Order = 1)]
public int var1;
```
```csharp
[Label("My Custom Header", skinStyle: SkinStyle.Box, Alignment = TextAnchor.MiddleCenter)]
public int var1;
```
```csharp
[Highlight(0, 1, 0)]
public int var1;
```
```csharp
[Help("Help information", Order = -1)]
public int var1;
```
```csharp
[ImageArea("https://img.itch.zone/aW1nLzE5Mjc3NzUucG5n/original/Viawjm.png", 150.0f)]
public int var1;
```

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc39.PNG)

#### ToolboxConditionDrawers

Enable/disable or show/hide properties using custom conditions. You can use them together with any other type of drawer.
Every ToolboxConditionDrawer supports boolean, int, string and enum types and works even with array/list properties.

```csharp
public string stringValue = "sho";
[EnableIf(nameof(stringValue), "show")] //or DisableIfAttribute
public int var1;
```

```csharp
public KeyCode enumValue = KeyCode.A;
[ShowIf(nameof(enumValue), KeyCode.A)] //or HideIfAttribute
public int var1;
```

```csharp
[Disable, ReorderableList]
public int[] vars1 = new [] { 1, 2, 3, 4 };
```

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc19.png)

#### InLineEditorAttribute

```csharp
[InLineEditor]
public Transform var1;
```
![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc32.png)
```csharp
[InLineEditor]
public AudioClip var1;
```
![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc36.png)
```csharp
[InLineEditor(drawPreview:true)]
public Material var1;
```
![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/Attributes/doc37.png)

## Reorderable List

Custom implementation of standard ReorderableList(UnityEditorInternal). Usable as an attribute in inspector fields or a single object in custom editors.

> Editor Toolbox/Editor/Internal/ReorderableList.cs

```csharp
var list = new ReorderableList(SerializedProperty property, string elementLabel, bool draggable, bool hasHeader, bool fixedSize);
```
```csharp
[ReorderableList(ListStyle.Lined, "Item")]
public List<int> linedStyleList;
```
![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/doc6.png)
```csharp
[ReorderableList(ListStyle.Round)]
public List<string> standardStyleList;
```
![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/doc7.png)
```csharp
[ReorderableList(ListStyle.Boxed, fixedSize: true)]
public GameObject[] boxedStyleList = new GameObject[4];
```
![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/doc8.png)

## Editor Extensions

### Hierarchy <a name="hierarchy"></a>

Enable and customize the presented hierarchy overlay in the **ToolboxEditorSettings**. Basically it provides more data about particular GameObjects directly within the Hierarchy window. Additionally, you can create special 'Header' objects using the '#h' prefix or Create menu: GameObject/Editor Toolbox/Hierarchy Header.

Each row can contain:
- Scripts information
- Layer
- Tag
- Toggle to enable/disable GameObject
- Icon

> Editor Toolbox/Editor/ToolboxEditorHierarchy.cs

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/doc2.png)

### Project <a name="project"></a>

Set custom folder icons in the **ToolboxEditorSettings**.

Properties that can be edited include:
- XY position and scale of the large icon
- XY position and scale of the small icon
- Path to directory or name (depends on picked item type)
- Optional tooltip
- Large icon
- Small icon

> Editor Toolbox/Editor/ToolboxEditorProject.cs

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/doc12.png)  

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/doc11.png)

### Toolbar <a name="toolbar"></a>

> Editor Toolbox/Editor/ToolboxEditorToolbar.cs

Check **Examples** for more details.

> Examples/Editor/SampleToolbar.cs

```csharp
using Toolbox.Editor;

[UnityEditor.InitializeOnLoad]
public static class MyEditorUtility
{
	static MyEditorUtility()
	{
		ToolboxEditorToolbar.OnToolbarGui += OnToolbarGui;
	}
	
	private static void OnToolbarGui()
	{
		GUILayout.FlexibleSpace();
		if (GUILayout.Button("1", Style.commandLeftStyle))
		{
			Debug.Log("1");
		}
		if (GUILayout.Button("2", Style.commandMidStyle))
		{
			Debug.Log("2");
		}
		if (GUILayout.Button("3", Style.commandMidStyle))
		{
			Debug.Log("3");
		}
		if (GUILayout.Button("4", Style.commandMidStyle))
		{
			Debug.Log("4");
		}
		if (GUILayout.Button("5", Style.commandRightStyle))
		{
			Debug.Log("5");
		}
	}
}
```

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/doc10.png)

### Utilities 

Copy and paste all components from/to particular GameObject.

![inspector](https://github.com/arimger/Unity-Editor-Toolbox/blob/develop/Documentation/doc13.png)

## Editor Extras

I decieded to move additional editors and tools to Gist.

### Prefab/GameObject Painter

Check it out [HERE](https://gist.github.com/arimger/00842a217ea8ab03d4e1b81f11592cf3)
