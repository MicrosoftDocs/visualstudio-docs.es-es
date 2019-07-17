---
title: Migración de extensibilidad del Diseñador XAML
ms.date: 07/09/2019
ms.topic: conceptual
author: lutzroeder
ms.author: lutzr
manager: jillfra
dev_langs:
- csharp
- vb
monikerRange: vs-2019
ms.openlocfilehash: 4485e9a11cb4770477374deed651fbff2df6df52
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67890314"
---
# <a name="xaml-designer-extensibility-migration"></a>Migración de extensibilidad del Diseñador XAML

En Visual Studio 2019, el Diseñador XAML admite dos arquitecturas diferentes: la arquitectura del Diseñador de aislamiento y la arquitectura de la superficie de aislamiento más reciente. Esta transición de la arquitectura es necesario para admitir tiempos de ejecución de destino que no se puede hospedar en un proceso de .NET Framework. Mover a la arquitectura de aislamiento superficie presenta cambios importantes en el modelo de extensibilidad de terceros. En este artículo se describe estos cambios que están disponibles en el canal de versión preliminar 16.2 de Visual Studio de 2019.

**Aislamiento de diseñador** se utiliza el Diseñador de WPF para los proyectos que tienen como destino .NET Framework y admite *. design.dll* extensiones. Las extensiones de terceros, bibliotecas de controles y código de usuario se cargan en un proceso externo (*XDesProc.exe*) junto con el código del diseñador real y los paneles de diseñador.

**Aislamiento de superficie** se usa el diseñador UWP. También se usa el Diseñador de WPF para los proyectos que tienen como destino .NET Core. De forma aislada expuesta, bibliotecas de código y el control de usuario solo se cargan en un proceso independiente, mientras el diseñador y sus paneles se cargan en el proceso de Visual Studio (*DevEnv.exe*). El tiempo de ejecución utilizado para la ejecución de las bibliotecas de código y el control de usuario es diferente del usado por .NET Framework para el diseñador real y el código de extensibilidad de terceros.

![arquitectura de migración de extensibilidad](media/xaml-designer-extensibility-migration-architecture.png)

Debido a esta transición de la arquitectura, las extensiones de terceros ya no se cargan en el mismo proceso que las bibliotecas de control de terceros. Las extensiones ya no pueden tener dependencias directas en las bibliotecas de control o acceder directamente a objetos en tiempo de ejecución. Las extensiones que se han escrito previamente para la arquitectura de diseñador aislamiento mediante el *Microsoft.Windows.Extensibility.dll* API se debe migrar a un nuevo enfoque para trabajar con la arquitectura de la superficie de aislamiento. En la práctica, una extensión existente debe compilarse con los nuevos ensamblados de la API de extensibilidad. Tipos de acceso al control de tiempo de ejecución a través de [typeof](/dotnet/csharp/language-reference/keywords/typeof) o las instancias en tiempo de ejecución deben reemplazarse o quitar porque ahora se cargan bibliotecas de controles en un proceso diferente.

## <a name="new-extensibility-api-assemblies"></a>Nuevos ensamblados de la API de extensibilidad

Los nuevos ensamblados de la API de extensibilidad son similares a los ensamblados de API de extensibilidad existentes, pero siguen un esquema de nomenclatura diferente para diferenciarlos. De forma similar, los nombres de espacio de nombres han cambiado para reflejar los nuevos nombres de ensamblado.

| Ensamblado de la API de diseñador aislamiento            | Ensamblado de aislamiento superficie de API                       |
|:------------------------------------------ |:---------------------------------------------------- |
| Microsoft.Windows.Design.Extensibility.dll | Microsoft.VisualStudio.DesignTools.Extensibility.dll |
| Microsoft.Windows.Design.Interaction.dll   | Microsoft.VisualStudio.DesignTools.Interaction.dll   |

## <a name="new-file-extension-and-discovery"></a>Detección y la nueva extensión de archivo

En lugar de usar el *. design.dll* nueva superficie se detectarán las extensiones mediante el uso de extensión de archivo del *. designtools.dll* la extensión de archivo. *. design.dll* y *. designtools.dll* extensiones pueden existir en la misma *diseño* subcarpeta.

Mientras se compilan las bibliotecas de controles de terceros para el tiempo de ejecución de destino real (.NET Core o UWP), el *. designtools.dll* extensión siempre se debe compilar como un ensamblado de .NET Framework.

## <a name="decouple-attribute-tables-from-runtime-types"></a>Desacoplar las tablas de atributos de tipos en tiempo de ejecución

El modelo de extensibilidad de la superficie de aislamiento no permite que las extensiones dependen de las bibliotecas de control real y, por lo tanto, las extensiones no pueden hacer referencia a tipos desde la biblioteca de controles. Por ejemplo, *MyLibrary.designtools.dll* no debe tener una dependencia en *MyLibrary.dll*.

Estas dependencias eran más comunes al registrar los metadatos de tipos a través de las tablas de atributos. Tipos de código de extensión que se hace referencia a la biblioteca de controles directamente a través de [typeof](/dotnet/csharp/language-reference/keywords/typeof) o [GetType](/dotnet/visual-basic/language-reference/operators/gettype-operator) se sustituye en las nuevas API mediante el uso de nombres de tipo basados en cadenas:

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

Proveedores de características se implementan en ensamblados de extensión y se cargan en el proceso de Visual Studio. `FeatureAttribute` seguirán haciendo referencia a tipos de proveedor de características directamente mediante [typeof](/dotnet/csharp/language-reference/keywords/typeof).

Actualmente, se admiten los siguientes proveedores de características:

* `DefaultInitializer`
* `AdornerProvider`
* `ContextMenuProvider`
* `ParentAdapter`
* `PlacementAdapter`

Dado que los proveedores de características ahora se cargan en un proceso diferente de las bibliotecas de código y control de tiempo de ejecución real, ya no son tener acceso directamente a objetos en tiempo de ejecución. En su lugar, todas las interacciones de este tipo deben convertirse para usar las API basadas en modelos correspondientes. La API del modelo se ha actualizado y el acceso a <xref:System.Type> o <xref:System.Object> sea ya no está disponible o se ha reemplazado por `TypeIdentifier` y `TypeDefinition`.

`TypeIdentifier` Representa una cadena sin un nombre de ensamblado que identifica un tipo. Un `TypeIdenfifier` se puede resolver como un `TypeDefinition` para consultar información adicional sobre el tipo. `TypeDefinition` no se almacenará en caché las instancias en el código de extensión.

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

Las API se quitan del conjunto de API de extensibilidad aislamiento superficie:

* `ModelFactory.CreateItem(EditingContext context, object item)`
* `ViewItem.PlatformObject`
* `ModelProperty.DefaultValue`

Las API que usan `TypeIdentifier` en lugar de <xref:System.Type>:

* `ModelFactory.CreateItem(EditingContext context, Type itemType, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, Type itemType, CreateOptions options, params object[] arguments)`
* `ModelFactory.CreateStaticMemberItem(EditingContext context, Type type, string memberName)`
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

Las API que usan `TypeIdentifier` en lugar de <xref:System.Type> y ya no admiten argumentos de constructor:

* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, CreateOptions options, params object[] arguments)`

Las API que usan `TypeDefinition` en lugar de <xref:System.Type>:

* `ModelFactory.ResolveType(EditingContext context, TypeIdentifier typeIdentifier)`
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

Las API que usan `ModelItem` en lugar de <xref:System.Object>:

* `ModelItemCollection.Insert(int index, object value)`
* `ModelItemCollection.Remove(object value)`
* `ModelItemDictionary.Add(object key, object value)`
* `ModelItemDictionary.ContainsKey(object key)`
* `ModelItemDictionary.Remove(object key)`
* `ModelItemDictionary.TryGetValue(object key, out ModelItem value)`

Conoce los tipos primitivos como `Int32`, `String`, o `Thickness` puede pasarse a la API del modelo como instancias de .NET Framework y se convertirá en el objeto correspondiente en el proceso de destino en tiempo de ejecución. Por ejemplo:

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

Más ejemplos de código están disponibles en el [xaml designer extensibility muestras](https://github.com/microsoft/xaml-designer-extensibility-samples) repositorio.

## <a name="limited-support-for-designdll-extensions"></a>Compatibilidad limitada. design.dll extensiones

Si cualquier *. designtools.dll* extensión se descubre para una biblioteca de controles, que se carga primero y detección de *. design.dll* extensiones se omite.

Si no hay ningún *. designtools.dll* extensiones están presentes, pero un *. design.dll* se encuentra la extensión, intente cargar este ensamblado para extraer la información de la tabla de atributos para admitir el servicio de lenguaje XAML el editor básico y escenarios de inspector de propiedad. Este mecanismo está limitado en el ámbito. No permite la carga de extensiones del Diseñador de aislamiento para ejecutar los proveedores de características, pero es posible que proporcionan compatibilidad básica para bibliotecas de controles WPF existentes.
