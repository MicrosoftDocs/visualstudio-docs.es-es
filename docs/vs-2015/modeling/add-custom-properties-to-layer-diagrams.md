---
title: Agregar propiedades personalizadas a diagramas de capas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, adding custom properties
ms.assetid: 52b3ac25-d10b-4507-a1fe-209ccb4d2777
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ec1c7c94c8a0e6aa233cf21f9b57e093cc430d48
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655289"
---
# <a name="add-custom-properties-to-layer-diagrams"></a>Agregar propiedades personalizadas a diagramas de capas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al escribir código de extensión para los diagramas de capas, puede almacenar valores en cualquier elemento de un diagrama de capas. Los valores se conservarán cuando el diagrama se guarde y se vuelva a abrir. También puede hacer que estas propiedades aparezcan en la ventana **propiedades** para que los usuarios puedan verlas y editarlas. Por ejemplo, puede permitir que los usuarios especifiquen una expresión regular para cada capa y escriban código de validación para comprobar que los nombres de las clases de cada capa se ajustan al patrón especificado por el usuario.

## <a name="properties-not-visible-to-the-user"></a>Propiedades no visibles para el usuario
 Si solo desea que el código asocie valores a cualquier elemento de un diagrama de capas, no es necesario definir un componente MEF. Hay un diccionario denominado `Properties` en [ILayerElement](/previous-versions/ff644511(v=vs.140)). Solo tiene que agregar valores que calculan referencias al diccionario de cualquier elemento de capa. Estos se guardarán como parte del diagrama de capas. Para obtener más información, vea [navegar y actualizar modelos de capas en el código del programa](../modeling/navigate-and-update-layer-models-in-program-code.md).

## <a name="properties-that-the-user-can-edit"></a>Propiedades que el usuario puede editar
 **Preparación inicial**

> [!IMPORTANT]
> Para que las propiedades aparezcan, debe realizar el cambio siguiente en todos los equipos donde desee que las propiedades de capa sean visibles.
>
>  1. Ejecute el Bloc de notas con **Ejecutar como administrador**. Abrir `%ProgramFiles%\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest`
>
>  2. Dentro del elemento `Content`, agregue:
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
>
>  3. En la sección **Visual Studio Tools** del menú Inicio de la aplicación de Visual Studio, Abra **símbolo del sistema para desarrolladores**.
>
>     Especifique:
>
>     `devenv /rootSuffix /updateConfiguration`
>
>     `devenv /rootSuffix Exp /updateConfiguration`
>
>  4. Reinicie Visual Studio.

 **Asegúrese de que el código se encuentra en un proyecto VSIX**

 Si la propiedad forma parte de un proyecto de validación, gesto o comando, no es necesario agregar nada. El código de la propiedad personalizada debe definirse en un proyecto de extensibilidad de Visual Studio definido como componente MEF. Para obtener más información, vea [Agregar comandos y gestos a diagramas de capas](../modeling/add-commands-and-gestures-to-layer-diagrams.md) o [agregar validación de arquitectura personalizada a diagramas de capas](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

 **Definir la propiedad personalizada**

 Para crear una propiedad personalizada, defina una clase como esta:

```
[Export(typeof(IPropertyExtension))]
public class MyProperty
      : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

 Puede definir propiedades en [ILayerElement](/previous-versions/ff644511(v=vs.140)) o en cualquiera de sus clases derivadas, entre las que se incluyen:

- `ILayerModel`: el modelo

- `ILayer`: cada capa

- `ILayerDependencyLink`: los vínculos entre las capas

- `ILayerComment`

- `ILayerCommentLink`

## <a name="example"></a>Ejemplo
 El siguiente código es un descriptor de propiedad personalizado típico. Define una propiedad booleana en el modelo de capas (`ILayerModel`) que permite al usuario proporcionar valores para un método de validación personalizado.

```
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
 [Ampliar diagramas de capas](../modeling/extend-layer-diagrams.md)
