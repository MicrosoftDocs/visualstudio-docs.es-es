---
title: Agregar propiedades personalizadas a diagramas de dependencia
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, adding custom properties
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 368d1a794f51d827aa62cc913039edda59ae7ae6
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33864195"
---
# <a name="add-custom-properties-to-dependency-diagrams"></a>Agregar propiedades personalizadas a diagramas de dependencia

Cuando se escribe código de extensión para los diagramas de dependencia, puede almacenar valores a cualquier elemento en un diagrama de dependencia. Los valores se conservarán cuando el diagrama se guarde y se vuelva a abrir. También puede hacer que estas propiedades aparecen en la **propiedades** ventana para que los usuarios pueden verlas y editarlas. Por ejemplo, puede permitir que los usuarios especifiquen una expresión regular para cada capa y escriban código de validación para comprobar que los nombres de las clases de cada capa se ajustan al patrón especificado por el usuario.

## <a name="non-visible-properties"></a>Propiedades no visibles

Si desea que el código asocie valores a cualquier elemento de un diagrama de dependencia, no es necesario definir un componente MEF. Hay un diccionario denominado `Properties` en <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>. Solo tiene que agregar valores que calculan referencias al diccionario de cualquier elemento de capa. Se guardará como parte del diagrama de dependencia. Para obtener más información, consulte [navegar y actualizar modelos en el código de programa de capas](../modeling/navigate-and-update-layer-models-in-program-code.md).

## <a name="editable-properties"></a>Propiedades editables

**Preparación inicial**

> [!IMPORTANT]
> Para que las propiedades aparezcan, realice el siguiente cambio en cada equipo donde desea que esté visible de propiedades de capa:
>
> 1. Ejecutar el Bloc de notas mediante **ejecutar como administrador**. Abra *%ProgramFiles%\Microsoft Visual Studio [versión] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest*.
> 2. Dentro de la **contenido** elemento, agregar:
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
> 3. En el **Visual Studio Tools** sección del menú de inicio de aplicación de Visual Studio, abra **símbolo**. Especifique:
>
>      `devenv /rootSuffix /updateConfiguration`
>
>      `devenv /rootSuffix Exp /updateConfiguration`
> 4. Reinicie Visual Studio.

**Asegúrese de que el código está en un proyecto VSIX**

Si la propiedad forma parte de un proyecto de validación, gesto o comando, no es necesario agregar nada. El código de la propiedad personalizada debe definirse en un proyecto de extensibilidad de Visual Studio definido como componente MEF. Para obtener más información, consulte [agregar comandos y gestos a diagramas de dependencia](../modeling/add-commands-and-gestures-to-layer-diagrams.md) o [agregar validación de arquitectura personalizada a diagramas de dependencia](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

**Definir la propiedad personalizada**

Para crear una propiedad personalizada, defina una clase como esta:

```csharp
[Export(typeof(IPropertyExtension))]
public class MyProperty : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

Puede definir propiedades en <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> o cualquiera de sus clases derivadas, entre las que se incluyen:

-   `ILayerModel`: el modelo

-   `ILayer`: cada capa

-   `ILayerDependencyLink`: los vínculos entre las capas

-   `ILayerComment`

-   `ILayerCommentLink`

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
