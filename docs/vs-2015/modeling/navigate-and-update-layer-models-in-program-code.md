---
title: Navegar y actualizar modelos de capas en el código del programa | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
ms.assetid: c60edc87-33ee-4964-a954-40069f9febf3
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 88ab52f1b06e6a2da94d17225bdb26ecec358a6c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668571"
---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Navegar y actualizar modelos de capas en el código del programa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se describen los elementos y relaciones en los modelos de capas por los que se puede navegar y que se pueden actualizar mediante código de programa. Para obtener más información sobre los diagramas de capas desde el punto de vista del usuario, vea [diagramas de capas: referencia](../modeling/layer-diagrams-reference.md) y [diagramas de capas: instrucciones](../modeling/layer-diagrams-guidelines.md).

 El modelo `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer` descrito en este tema sirve de escaparate a un modelo <xref:Microsoft.VisualStudio.GraphModel>, de naturaleza mucho más general. Si está escribiendo un [comando de menú o una extensión de gestos](../modeling/add-commands-and-gestures-to-layer-diagrams.md), utilice el `Layer` modelo. Si está escribiendo una [extensión de validación de capas](../modeling/add-custom-architecture-validation-to-layer-diagrams.md), es más fácil usar `GraphModel` .

## <a name="transactions"></a>Transacciones
 Cuando actualice un modelo, considere insertar los cambios en una `ILinkedUndoTransaction`. Esto hace que los cambios estén condensados en una única transacción. Si alguno de los cambios no se produjera, se revertirá la transacción entera. Si el usuario deshace un cambio, todos los demás cambios también se desharán.

 Para obtener más información, vea [vincular actualizaciones del modelo UML mediante transacciones](../modeling/link-uml-model-updates-by-using-transactions.md).

```
using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("a name"))
{
    // Make changes here ....
    t.Commit(); // Don't forget this!
}
```

## <a name="containment"></a>Containment
 ![Tanto ILayer como ILayerModel pueden contener ILayers.](../modeling/media/layerapi-containment.png "LayerApi_Containment")

 Las capas ([ILayer](/previous-versions/ff644251(v=vs.140))) y el modelo de capas ([ILayerModel](/previous-versions/ff643069(v=vs.140))) pueden contener comentarios y capas.

 Una capa (`ILayer`) puede incluirse en un modelo de capas (`ILayerModel`) o anidarse en otra `ILayer`.

 Para crear un comentario o una capa, use los métodos de creación pertinentes del contenedor adecuado.

## <a name="dependency-links"></a>Vínculos de dependencias
 Un vínculo de dependencia se representa mediante un objeto. La navegación puede producirse en cualquier dirección:

 ![Un objeto ILayerDependencyLink conecta dos ILayers.](../modeling/media/layerapi-dependency.png "LayerApi_Dependency")

 Llame a `source.CreateDependencyLink(target)` para crear un vínculo de dependencia.

## <a name="comments"></a>Comentarios
 Los comentarios pueden incluirse en capas o en el modelo de capas, así como vincularse a cualquier elemento de capa:

 ![Se pueden adjuntar comentarios a cualquier elemento de capa.](../modeling/media/layerapi-comments.png "LayerApi_Comments")

 Un comentario puede estar vinculado a cualquier número de elementos o a ninguno.

 Use lo siguiente para obtener los comentarios adjuntos a un elemento de capa:

```csharp
ILayerModel model = diagram.GetLayerModel();
IEnumerable<ILayerComment> comments =
   model.Comments.Where(comment =>
      comment.Links.Any(link => link.Target == layerElement));

```

> [!CAUTION]
> La propiedad `Comments` de `ILayer` obtiene los comentarios incluidos en `ILayer`, pero no los comentarios vinculados a dicha capa.

 Para crear un comentario, invoque a `CreateComment()` en el contenedor correspondiente.

 Para crear un vínculo, use `CreateLink()` en el comentario.

## <a name="layer-elements"></a>Elementos de capa
 Todos los tipos de elemento que se pueden incluir en un modelo son elementos de capa:

 ![Lo que contiene el diagrama de capas son ILayerElements.](../modeling/media/layerapi-layerelements.png "LayerApi_LayerElements")

## <a name="properties"></a>Propiedades
 Cada `ILayerElement` tiene un diccionario de cadenas denominado `Properties`. Este diccionario se puede usar para incorporar información arbitraria acerca de cualquier elemento de capa.

## <a name="artifact-references"></a>Referencias de artefacto
 Una referencia de artefacto ([ILayerArtifactReference](/previous-versions/ff644536(v=vs.140))) representa el vínculo entre una capa y un elemento de proyecto, como un archivo, una clase o una carpeta. El usuario crea artefactos cuando crea una capa o le agrega elementos arrastrándolos desde el explorador de soluciones, la vista de clases o el examinador de objetos en un diagrama de capas. Se puede vincular a una capa un número indeterminado de referencias de artefacto.

 Cada fila del Explorador de capas muestra una referencia de artefacto. Para obtener más información, vea [crear diagramas de capas a partir del código](../modeling/create-layer-diagrams-from-your-code.md).

 Los métodos y tipos principales relacionados con las referencias de artefactos son los siguientes:

 [ILayerArtifactReference](/previous-versions/ff644536(v=vs.140)). La propiedad Categories indica el tipo de artefacto al que se está haciendo referencia, como una clase, un archivo ejecutable o un ensamblado. Las categorías establecen la forma en la que el identificador va a distinguir el artefacto de destino.

 [ArtifactReferenceExtensions. CreateArtifactReferenceAsync](/previous-versions/ff695840(v=vs.140)) crea una referencia de artefacto desde <xref:EnvDTE.Project> o <xref:EnvDTE.ProjectItem> . Se trata de una operación asincrónica, por lo que se suele proporcionar una devolución de llamada a la que se llama cuando la creación ha finalizado.

 Las referencias de artefacto de capa no se deben confundir con los artefactos de los diagramas de casos de uso.

## <a name="shapes-and-diagrams"></a>Formas y diagramas
 Se usan dos objetos para representar cada elemento en un modelo de capas: `ILayerElement` y un [IShape](/previous-versions/ee806673(v=vs.140)). `IShape` señala la posición y el tamaño de la forma en el diagrama. En los modelos de capas, cada `ILayerElement` tiene un `IShape` y cada `IShape` en el diagrama de capas tiene un `ILayerElement`. `IShape` también se usa en los modelos UML. Por lo tanto, no todos los `IShape` poseen un elemento de capa.

 Del mismo modo, `ILayerModel` se muestra en un [IDiagram](/previous-versions/ee789658(v=vs.140)).

 En el código de un controlador de gesto o comando personalizado se puede obtener el diagrama actual y la selección de formas actual de la importación de `DiagramContext`:

```
public class ... {
[Import]
    public IDiagramContext DiagramContext { get; set; }
...
public void ... (...)
{ IDiagram diagram = this.DiagramContext.CurrentDiagram;
  ILayerModel model = diagram.GetLayerModel();
  if (model != null)
  { foreach (ILayer layer in model.Layers) { ... }}
  foreach (IShape selected in diagram.SelectedShapes)
  { ILayerElement element = selected.GetLayerElement();
    if (element != null) ... }}
```

 ![Cada ILayerElement se presenta mediante un objeto IShape.](../modeling/media/layerapi-shapes.png)

 [IShape](/previous-versions/ee806673(v=vs.140)) y [IDiagram](/previous-versions/ee789658(v=vs.140)) también se usan para mostrar modelos UML. Para obtener más información, vea [Mostrar un modelo UML en diagramas](../modeling/display-a-uml-model-on-diagrams.md).

## <a name="see-also"></a>Consulte también

- [Agregar comandos y gestos a diagramas de capas](../modeling/add-commands-and-gestures-to-layer-diagrams.md)
- [Agregar validación de arquitectura personalizada a diagramas de capas](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
- [Agregar propiedades personalizadas a diagramas de capas](../modeling/add-custom-properties-to-layer-diagrams.md)
- [Diagramas de capas: referencia](../modeling/layer-diagrams-reference.md)
- [Diagrama de capas: instrucciones](../modeling/layer-diagrams-guidelines.md)
- [Ampliar modelos y diagramas UML](../modeling/extend-uml-models-and-diagrams.md)
