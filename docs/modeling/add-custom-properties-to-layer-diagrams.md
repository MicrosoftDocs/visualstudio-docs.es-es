---
title: Agregar propiedades personalizadas a diagramas de dependencia
description: Obtenga información sobre cómo almacenar valores con cualquier elemento en un diagrama de dependencias al escribir código de extensión para diagramas de dependencias.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency diagrams, adding custom properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 70588a2d472a1170b58911eece4fa70831064f72
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389857"
---
# <a name="add-custom-properties-to-dependency-diagrams"></a>Agregar propiedades personalizadas a diagramas de dependencia

Al escribir código de extensión para diagramas de dependencias, puede almacenar valores con cualquier elemento en un diagrama de dependencias. Los valores se conservarán cuando el diagrama se guarde y se vuelva a abrir. También puede hacer que estas propiedades aparezcan en la **ventana Propiedades** para que los usuarios puedan verlas y editarlas. Por ejemplo, puede permitir que los usuarios especifiquen una expresión regular para cada capa y escriban código de validación para comprobar que los nombres de las clases de cada capa se ajustan al patrón especificado por el usuario.

## <a name="non-visible-properties"></a>Propiedades no visibles

Si solo desea que el código adjunte valores a cualquier elemento de un diagrama de dependencias, no es necesario definir un componente MEF. Hay un diccionario denominado `Properties` en [ILayerElement](/previous-versions/ff644511(v=vs.140)). Solo tiene que agregar valores que calculan referencias al diccionario de cualquier elemento de capa. Se guardarán como parte del diagrama de dependencias.

## <a name="editable-properties"></a>Propiedades editables

**Preparación inicial**

> [!IMPORTANT]
> Para que aparezcan las propiedades, realice el siguiente cambio en cada equipo en el que desee que las propiedades de capa sean visibles:
>
> 1. Ejecute el Bloc de notas mediante **Ejecutar como administrador.** Abra *%ProgramFiles%\Microsoft Visual Studio [versión]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest*.
> 2. Dentro del **elemento Content,** agregue:
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
>
> 3. En la **Visual Studio Tools** del menú inicio Visual Studio aplicación, **abra Símbolo del sistema para desarrolladores**. Especifique:
>
>      `devenv /rootSuffix /updateConfiguration`
>
>      `devenv /rootSuffix Exp /updateConfiguration`
> 4. Reinicie Visual Studio.

**Asegurarse de que el código está en un proyecto VSIX**

Si la propiedad forma parte de un proyecto de comando, gesto o validación, no es necesario agregar nada. El código de la propiedad personalizada debe definirse en un proyecto de extensibilidad de Visual Studio definido como componente MEF. Para obtener más información, vea [Agregar comandos y gestos](../modeling/add-commands-and-gestures-to-layer-diagrams.md) a diagramas de dependencias o Agregar validación de arquitectura personalizada a [diagramas de dependencias.](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

**Definir la propiedad personalizada**

Para crear una propiedad personalizada, defina una clase como esta:

```csharp
[Export(typeof(IPropertyExtension))]
public class MyProperty : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

Puede definir propiedades en [ILayerElement](/previous-versions/ff644511(v=vs.140)) o en cualquiera de sus clases derivadas, entre las que se incluyen:

- `ILayerModel` : el modelo

- `ILayer` - cada capa

- `ILayerDependencyLink`: los vínculos entre las capas

- `ILayerComment`

- `ILayerCommentLink`

## <a name="example"></a>Ejemplo

El siguiente código es un descriptor de propiedad personalizado típico. Define una propiedad booleana en el modelo de capas (`ILayerModel`) que permite al usuario proporcionar valores para un método de validación personalizado.

```csharp
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;

namespace MyNamespace
{
  /// <summary>
  /// Custom properties are added to the Layer Designer via a custom
  /// Property Descriptor. We have to export this Property Descriptor
  /// using MEF to make it available in the Layer Designer.
  /// </summary>
  [Export(typeof(IPropertyExtension))]
  public class AllTypesMustBeReferencedProperty
      : PropertyExtension<ILayerModel>
  {
    /// <summary>
    /// Each custom property must have a unique name.
    /// Usually we use the full name of this class.
    /// </summary>
    public static readonly string FullName =
      typeof(AllTypesMustBeReferencedProperty).FullName;

    /// <summary>
    /// Construct the property. Notice the use of FullName.
    /// </summary>
    public AllTypesMustBeReferencedProperty()
            : base(FullName)
    {  }

    /// <summary>
    /// The display name is shown in the Properties window.
    /// We therefore use a localizable resource.
    /// </summary>
    public override string DisplayName
    {
      get { return Strings.AllTypesMustBeReferencedDisplayName; }
    }

    /// <summary>
    /// Description shown at the bottom of the Properties window.
    /// We use a resource string for easier localization.
    /// </summary>
    public override string Description
    {
      get { return Strings.AllTypesMustBeReferencedDescription; }
    }

    /// <summary>
    /// This is called to set a new value for this property. We must
    /// throw an exception if the value is invalid.
    /// </summary>
    /// <param name="component">The target ILayerElement</param>
    /// <param name="value">The new value</param>
    public override void SetValue(object component, object value)
    {
      ValidateValue(value);
      base.SetValue(component, value);
    }
    /// <summary>
    /// Helper to validate the value.
    /// </summary>
    /// <param name="value">The value to validate</param>
    private static void ValidateValue(object value)
    {  }

    public override Type PropertyType
    { get { return typeof(bool); } }

    /// <summary>
    /// The segment label of the properties window.
    /// </summary>
    public override string Category
    {
      get
      {
        return Strings.AllTypesMustBeReferencedCategory;
      }
    }
  }
}
```

## <a name="see-also"></a>Vea también

- [Ampliación de diagramas de dependencia](../modeling/extend-layer-diagrams.md)
