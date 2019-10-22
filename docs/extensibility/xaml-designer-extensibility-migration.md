---
title: Migración de extensibilidad de Diseñador XAML
ms.date: 07/09/2019
ms.topic: conceptual
author: lutzroeder
ms.author: lutzr
manager: jillfra
dev_langs:
- csharp
- vb
monikerRange: vs-2019
ms.openlocfilehash: 9f5085c7a655f186c3c8a4a6eecada8b440650cd
ms.sourcegitcommit: 528178a304e66c0cb7ab98b493fe3c409f87493a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273218"
---
# <a name="xaml-designer-extensibility-migration"></a>Migración de extensibilidad del diseñador XAML

En Visual Studio 2019, el diseñador XAML admite dos arquitecturas diferentes: la arquitectura de aislamiento del diseñador y la arquitectura de aislamiento de superficie más reciente. Esta transición de arquitectura es necesaria para admitir los tiempos de ejecución de destino que no se pueden hospedar en un proceso de .NET Framework. Al pasar a la arquitectura de aislamiento de superficie, se introducen cambios importantes en el modelo de extensibilidad de terceros. En este artículo se describen estos cambios, que están disponibles en Visual Studio 2019 a partir de la versión 16,3.

El diseñador de WPF usa el **aislamiento de diseñador** para los proyectos que tienen como destino el .NET Framework y admiten las extensiones. *Design. dll* . El código de usuario, las bibliotecas de control y las extensiones de terceros se cargan en un proceso externo (*XDesProc. exe*) junto con el código y los paneles del diseñador reales.

El diseñador UWP usa el **aislamiento de superficie** . El diseñador de WPF también lo usa para los proyectos que tienen como destino .NET Core. En el aislamiento de superficie, solo se cargan el código de usuario y las bibliotecas de control en un proceso independiente, mientras que el diseñador y sus paneles se cargan en el proceso de Visual Studio (*DevEnv. exe*). El tiempo de ejecución que se usa para ejecutar el código de usuario y las bibliotecas de controles es diferente del que utiliza el .NET Framework para el diseñador real y el código de extensibilidad de terceros.

![extensibilidad: arquitectura de migración](media/xaml-designer-extensibility-migration-architecture.png)

Debido a esta transición de arquitectura, las extensiones de terceros ya no se cargan en el mismo proceso que las bibliotecas de control de terceros. Las extensiones ya no pueden tener dependencias directas en bibliotecas de controles ni tener acceso directamente a objetos en tiempo de ejecución. Las extensiones que se escribieron previamente para la arquitectura de aislamiento de diseñador mediante la API *Microsoft. Windows. Extensibility. dll* se deben migrar a un nuevo enfoque para trabajar con la arquitectura de aislamiento de superficie. En la práctica, se debe compilar una extensión existente con los nuevos ensamblados de la API de extensibilidad. El acceso a los tipos de control en tiempo de ejecución a través de [typeof](/dotnet/csharp/language-reference/keywords/typeof) o instancias en tiempo de ejecución se debe reemplazar o quitar, ya que las bibliotecas de control ahora se cargan en un proceso diferente.

## <a name="new-extensibility-api-assemblies"></a>Nuevos ensamblados de API de extensibilidad

Los nuevos ensamblados de API de extensibilidad son similares a los ensamblados de la API de extensibilidad existentes, pero siguen un esquema de nomenclatura diferente para diferenciarlos. Del mismo modo, los nombres de los espacios de nombres han cambiado para reflejar los nuevos nombres de ensamblado.

| Ensamblado de API de aislamiento del diseñador            | Ensamblado de API de aislamiento de superficie                       |
|:------------------------------------------ |:---------------------------------------------------- |
| Microsoft.Windows.Design.Extensibility.dll | Microsoft.VisualStudio.DesignTools.Extensibility.dll |
| Microsoft.Windows.Design.Interaction.dll   | Microsoft.VisualStudio.DesignTools.Interaction.dll   |

## <a name="new-file-extension-and-discovery"></a>Nueva extensión de archivo y detección

En lugar de utilizar la extensión de archivo *. Design. dll* , se detectarán nuevas extensiones de Surface mediante la extensión de archivo *. designtools. dll* . las extensiones. *Design. dll* y *. designtools. dll* pueden existir en la misma subcarpeta de *diseño* .

Mientras que las bibliotecas de control de terceros se compilan para el tiempo de ejecución de destino real (.NET Core o UWP), la extensión *. designtools. dll* se debe compilar siempre como un ensamblado de .NET Framework.

## <a name="decouple-attribute-tables-from-run-time-types"></a>Desacoplar tablas de atributos de tipos en tiempo de ejecución

El modelo de extensibilidad de aislamiento de superficie no permite que las extensiones dependan de las bibliotecas de control reales y, por lo tanto, las extensiones no pueden hacer referencia a los tipos de la biblioteca de controles. Por ejemplo, *myLibrary. designtools. dll* no debe tener una dependencia en *myLibrary. dll*.

Estas dependencias eran más comunes al registrar metadatos para tipos a través de tablas de atributos. El código de extensión que hace referencia a los tipos de biblioteca de controles directamente a través de [typeof](/dotnet/csharp/language-reference/keywords/typeof) o [GetType](/dotnet/visual-basic/language-reference/operators/gettype-operator) se sustituye en las nuevas API mediante el uso de nombres de tipo basados en cadenas:

```csharp
using Microsoft.VisualStudio.DesignTools.Extensibility.Metadata;
using Microsoft.VisualStudio.DesignTools.Extensibility.Features;
using Microsoft.VisualStudio.DesignTools.Extensibility.Model;

[assembly: ProvideMetadata(typeof(AttributeTableProvider))]

public class AttributeTableProvider : IProvideAttributeTable
{
  public AttributeTable AttributeTable
  {
    get
    {
      var builder = new AttributeTableBuilder();
      builder.AddCustomAttributes("MyLibrary.MyControl", new DescriptionAttribute(Strings.MyControlDescription);
      builder.AddCustomAttributes("MyLibrary.MyControl", new FeatureAttribute(typeof(MyControlDefaultInitializer));
      return builder.CreateTable();
    }
  }
}
```

```vb
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Metadata
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Features
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Model

<Assembly: ProvideMetadata(GetType(AttributeTableProvider))>

Public Class AttributeTableProvider
    Implements IProvideAttributeTable

    Public ReadOnly Property AttributeTable As AttributeTable Implements IProvideAttributeTable.AttributeTable
        Get
            Dim builder As New AttributeTableBuilder
            builder.AddCustomAttributes("MyLibrary.MyControl", New DescriptionAttribute(Strings.MyControlDescription))
            builder.AddCustomAttributes("MyLibrary.MyControl", New FeatureAttribute(GetType(MyControlDefaultInitializer)))
            Return builder.CreateTable()
        End Get
    End Property
End Class
```

## <a name="feature-providers-and-model-api"></a>Proveedores de características y API de modelo

Los proveedores de características se implementan en ensamblados de extensión y se cargan en el proceso de Visual Studio. `FeatureAttribute`seguirá haciendo referencia a los tipos de proveedor de características directamente mediante [typeof](/dotnet/csharp/language-reference/keywords/typeof).

Actualmente, se admiten los siguientes proveedores de características:

* `DefaultInitializer`
* `AdornerProvider`
* `ContextMenuProvider`
* `ParentAdapter`
* `PlacementAdapter`
* `DesignModeValueProvider`es compatible con la limitación a `TranslatePropertyValue` la que se llamará a través `InvalidateProperty` de o cuando se modifique en el diseñador. No se llamará cuando se modifique en el código en tiempo de ejecución.

Dado que los proveedores de características se cargan en un proceso diferente del código y las bibliotecas de control reales en tiempo de ejecución, ya no pueden tener acceso a los objetos en tiempo de ejecución directamente. En su lugar, todas estas interacciones deben convertirse para usar las API basadas en modelos correspondientes. La API de modelo se ha actualizado y el acceso <xref:System.Type> a <xref:System.Object> o ya no está disponible o se ha reemplazado `TypeIdentifier` por `TypeDefinition`y.

`TypeIdentifier`representa una cadena sin un nombre de ensamblado que identifica un tipo. Un `TypeIdenfifier` se puede resolver `TypeDefinition` como para consultar información adicional sobre el tipo. `TypeDefinition`las instancias no se pueden almacenar en caché en el código de la extensión.

```csharp
TypeDefinition type = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("MyLibrary.MyControl"));
TypeDefinition buttonType = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("System.Windows.Controls.Button"));
if (type?.IsSubclassOf(buttonType) == true)
{
}
```

```vb
Dim type As TypeDefinition = ModelFactory.ResolveType(
    item.Context, New TypeIdentifier("MyLibrary.MyControl"))
Dim buttonType As TypeDefinition = ModelFactory.ResolveType(
    item.Context, New TypeIdentifier("System.Windows.Controls.Button"))
If type?.IsSubclassOf(buttonType) Then

End If
```

API quitadas del conjunto de API de extensibilidad de aislamiento de Surface:

* `ModelFactory.CreateItem(EditingContext context, object item)`
* `ViewItem.PlatformObject`
* `ModelProperty.DefaultValue`
* `AssemblyReferences.GetTypes(Type baseType)`

API que usan `TypeIdentifier` en lugar de <xref:System.Type>:

* `ModelFactory.CreateItem(EditingContext context, Type itemType, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, Type itemType, CreateOptions options, params object[] arguments)`
* `ModelFactory.CreateStaticMemberItem(EditingContext context, Type type, string memberName)`
* Cambio de `ModelFactory.ResolveType(EditingContext context, Type)` a `MetadataFactory.ResolveType(EditingContext context, TypeIdentifier typeIdentifier)`
* Cambio de `ModelService.ResolveType(TypeIdentifier typeIdentifier)` a `MetadataService.ResolveType(TypeIdentifier typeIdentifier)`
* `ViewItem.ItemType`
* `ModelEvent.EventType`
* `ModelEvent.IsEventOfType(Type type)`
* `ModeItem.IsItemOfType(Type type)`
* `ModelParent.CanParent(EditingContext context, ModelItem parent, Type childType)`
* `ModelParent.FindParent(EditingContext context, Type childType, ModelItem startingItem)`
* `ModelParent.FindParent(Type childType, GestureData gestureData)`
* `ModelProperty.IsPropertyOfType(Type type)`
* `ParentAdpater.CanParent(ModelItem parent, Type childType)`
* `ParentAdapter.RedirectParent(ModelItem parent, Type childType)`

Las API que `TypeIdentifier` utilizan en lugar <xref:System.Type> de y ya no admiten argumentos de constructor:

* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, CreateOptions options, params object[] arguments)`

API que usan `TypeDefinition` en lugar de <xref:System.Type>:

* `ValueTranslationService.GetProperties(Type itemType)`
* `ValueTranslationService.HasValueTranslation(Type itemType, PropertyIdentifier identifier)`
* `ValueTranslationService.TranslatePropertyValue(Type itemType, ModelItem item, PropertyIdentifier identifier, object value)`
* `ModelService.Find(ModelItem startingItem, Type type)`
* `ModelService.Find(ModelItem startingItem, Predicate<Type> match)`
* `ModelItem.ItemType`
* `ModelProperty.AttachedOwnerType`
* `ModelProperty.PropertyType`
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type)`
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type, Predicate<Type> match)`
* `FeatureManager.InitializeFeatures(Type type)`
* `FeatureManager.GetCustomAttributes(Type type, Type attributeType)`
* `AdapterService.GetAdapter<TAdapterType>(Type itemType)`
* `AdapterService.GetAdapter(Type adapterType, Type itemType)`
* `PropertyEntry.PropertyType`

API que usan `AssemblyIdentifier` en lugar de `<xref:System.Reflection.AssemblyName?displayProperty=fullName>`:

* `AssemblyReferences.ReferencedAssemblies`
* Cambio de `AssemblyReferences.LocalAssemblyName` a `AssemblyReferences.LocalAssemblyIdentifier`

Además, `ModelItem` las API `SetValue` como solo admiten instancias de tipos primitivos o tipos de .NET Framework integrados que se pueden convertir para el tiempo de ejecución de destino. Actualmente se admiten estos tipos:

* Tipos de `Boolean`.NET Framework primitivos: `Char`, `DateTime` `Byte`, `Double`, `Enum`,, ,`Int16` ,,`Int32` ,`SByte` ,, `Guid` `Int64` `Nullable` , `Single`, `String`, `Type`, `UInt16`, `UInt32`, `UInt64`,`Uri`
* Tipos de .NET Framework de WPF conocidos (y tipos derivados `Brush`) `Color`: `CompositeTransform`, `CornerRadius`, `Duration`, `EasingFunctionBase`, `EasingMode`, `EllipseGeometry`, `FontFamily`, `GeneralTransform`, `Geometry` ,, , `GradientStopCollection`, `GradientStop`, `GridLength`, `ImageSource`, `InlineCollection`, `Inline`, `KeySpline`, `Material`, `Matrix`, `PathFigureCollection`, `PathFigure`, `PathSegmentCollection`, `PathSegment`, `Path`, `PointCollection`, `Point`, `PropertyPath`, `Rect`, `RepeatBehavior`, `Setter`, `Size`, `StaticResource`, `TextAlignment`, `TextDecorationCollection`, `ThemeResourceExtension`, `Thickness`, `TimeSpan`, `Transform3D`,`TransformCollection`

Por ejemplo:

```csharp
using Microsoft.VisualStudio.DesignTools.Extensibility.Features;
using Microsoft.VisualStudio.DesignTools.Extensibility.Model;

public class MyControlDefaultInitializer : DefaultInitializer
{
  public override void InitializeDefaults(ModelItem item)
  {
    item.Properties["Width"].SetValue(800d);
    base.InitializeDefaults(item);
  }
}
```

```vb
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Features
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Model

Public Class MyControlDefaultInitializer
    Inherits DefaultInitializer

    Public Overrides Sub InitializeDefaults(item As ModelItem)
        item.Properties!Width.SetValue(800.0)
        MyBase.InitializeDefaults(item)
    End Sub
End Class
```

Puede encontrar más ejemplos de código en el repositorio [XAML-Designer-Extensibility-samples](https://github.com/microsoft/xaml-designer-extensibility-samples) .

## <a name="limited-support-for-designdll-extensions"></a>Compatibilidad limitada para las extensiones. Design. dll

Si se detecta alguna extensión *. designtools. dll* para una biblioteca de controles, se carga primero y la detección de las extensiones *. Design. dll* se omite.

Si no hay extensiones *. designtools. dll* presentes pero se encuentra una extensión *. Design. dll* , el servicio de lenguaje XAML intenta cargar este ensamblado para extraer la información de la tabla de atributos para admitir escenarios básicos del editor y del inspector de propiedad. Este mecanismo está limitado en el ámbito. No permite la carga de extensiones de aislamiento del diseñador para ejecutar proveedores de características, pero puede proporcionar compatibilidad básica con las bibliotecas de controles WPF existentes.
