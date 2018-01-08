---
title: "Navegar y actualizar modelos de capas en el código de programa | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
ms.assetid: c60edc87-33ee-4964-a954-40069f9febf3
caps.latest.revision: "20"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.workload: multiple
ms.openlocfilehash: a9350a7aa2ed3b4befaa2305042dbc4fc74fcf31
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Navegar y actualizar modelos de capas en el código del programa
En este tema se describen los elementos y relaciones en los modelos de capas por los que se puede navegar y que se pueden actualizar mediante código de programa. Para obtener más información acerca de los diagramas de dependencia de punto de vista del usuario, consulte [diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md) y [diagramas de dependencia: directrices](../modeling/layer-diagrams-guidelines.md).  
  
 El <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer> modelo descrito en este tema es una fachada en general más <xref:Microsoft.VisualStudio.GraphModel> modelo. Si está escribiendo un [extensión de gesto o comando de menú](../modeling/add-commands-and-gestures-to-layer-diagrams.md), use el `Layer` modelo. Si está escribiendo un [extensión de validación de capas](../modeling/add-custom-architecture-validation-to-layer-diagrams.md), resulta más fácil de usar el `GraphModel`.  
  
## <a name="transactions"></a>Transacciones  
 Cuando actualice un modelo, considere insertar los cambios en una `ILinkedUndoTransaction`. Esto hace que los cambios estén condensados en una única transacción. Si alguno de los cambios no se produjera, se revertirá la transacción entera. Si el usuario deshace un cambio, todos los demás cambios también se desharán.  
  
```  
using (ILinkedUndoTransaction t =  
        LinkedUndoContext.BeginTransaction("a name"))  
{   
    // Make changes here ....  
    t.Commit(); // Don't forget this!  
}  
```  
  
## <a name="containment"></a>Inclusiones  
 ![Tanto ILayer como ILayerModel pueden contener ILayers. ] (../modeling/media/layerapi_containment.png "LayerApi_Containment")  
  
 Las capas (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayer>) y el modelo de capas (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>) pueden incluir comentarios y capas.  
  
 Una capa (`ILayer`) puede incluirse en un modelo de capas (`ILayerModel`) o anidarse en otra `ILayer`.  
  
 Para crear un comentario o una capa, use los métodos de creación pertinentes del contenedor adecuado.  
  
## <a name="dependency-links"></a>Vínculos de dependencias  
 Un vínculo de dependencia se representa mediante un objeto. La navegación puede producirse en cualquier dirección:  
  
 ![Un objeto ILayerDependencyLink conecta dos ILayers. ] (../modeling/media/layerapi_dependency.png "LayerApi_Dependency")  
  
 Llame a `source.CreateDependencyLink(target)` para crear un vínculo de dependencia.  
  
## <a name="comments"></a>Comentarios  
 Los comentarios pueden incluirse en capas o en el modelo de capas, así como vincularse a cualquier elemento de capa:  
  
 ![Se pueden adjuntar comentarios a cualquier elemento de capa. ] (../modeling/media/layerapi_comments.png "LayerApi_Comments")  
  
 Un comentario puede estar vinculado a cualquier número de elementos o a ninguno.  
  
 Use lo siguiente para obtener los comentarios adjuntos a un elemento de capa:  
  
```csharp  
ILayerModel model = diagram.GetLayerModel();   
IEnumerable<ILayerComment> comments =   
   model.Comments.Where(comment =>   
      comment.Links.Any(link => link.Target == layerElement));  
  
```  
  
> [!CAUTION]
>  La propiedad `Comments` de `ILayer` obtiene los comentarios incluidos en `ILayer`, pero no los comentarios vinculados a dicha capa.  
  
 Para crear un comentario, invoque a `CreateComment()` en el contenedor correspondiente.  
  
 Para crear un vínculo, use `CreateLink()` en el comentario.  
  
## <a name="layer-elements"></a>Elementos de capa  
 Todos los tipos de elemento que se pueden incluir en un modelo son elementos de capa:  
  
 ![dependencia diagrama son ILayerElements. ] (../modeling/media/layerapi_layerelements.png "LayerApi_LayerElements")  
  
## <a name="properties"></a>Propiedades  
 Cada `ILayerElement` tiene un diccionario de cadenas denominado `Properties`. Este diccionario se puede usar para incorporar información arbitraria acerca de cualquier elemento de capa.  
  
## <a name="artifact-references"></a>Referencias de artefacto  
 Una referencia de artefacto (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>) representa el vínculo entre una capa y un elemento del proyecto, como un archivo, una clase o una carpeta. El usuario crea artefactos al crear una capa o agregarle al arrastrar elementos desde el Explorador de soluciones, vista de clases y Examinador de objetos a un diagrama de dependencia. Se puede vincular a una capa un número indeterminado de referencias de artefacto.  
  
 Cada fila del Explorador de capas muestra una referencia de artefacto. Para obtener más información, consulte [crear diagramas de dependencia desde el código](../modeling/create-layer-diagrams-from-your-code.md).  
  
 Los métodos y tipos principales relacionados con las referencias de artefactos son los siguientes:  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>. La propiedad Categories indica el tipo de artefacto al que se está haciendo referencia, como una clase, un archivo ejecutable o un ensamblado. Las categorías establecen la forma en la que el identificador va a distinguir el artefacto de destino.  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ArtifactReferenceExtensions.CreateArtifactReferenceAsync%2A> crea una referencia de artefacto a partir de un <xref:EnvDTE.Project> o de un <xref:EnvDTE.ProjectItem>. Se trata de una operación asincrónica, por lo que se suele proporcionar una devolución de llamada a la que se llama cuando la creación ha finalizado.  
  
 Las referencias de artefacto de capa no se deben confundir con los artefactos de los diagramas de casos de uso.  
  
## <a name="shapes-and-diagrams"></a>Formas y diagramas  
 Se usan dos objetos para representar a cada elemento en un modelo de capas: <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> y <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape>. `IShape` señala la posición y el tamaño de la forma en el diagrama. En los modelos de capas, cada `ILayerElement` tiene uno `IShape`y cada `IShape` en una dependencia diagrama tiene un `ILayerElement`. `IShape` también se usa en los modelos UML. Por lo tanto, no todos los `IShape` poseen un elemento de capa.  
  
 De igual modo, el <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel> se muestra en un <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram>.  
  
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
  
 ![Cada ILayerElement se presenta mediante un objeto IShape. ] (../modeling/media/layerapi_shapes.png "LayerApi_Shapes")  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape> y <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram> también se usan para mostrar modelos UML. 
  
## <a name="see-also"></a>Vea también  
 [Agregar comandos y gestos a diagramas de dependencia](../modeling/add-commands-and-gestures-to-layer-diagrams.md)   
 [Agregar validación de arquitectura personalizada a diagramas de dependencia](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)   
 [Agregar propiedades personalizadas a diagramas de dependencia](../modeling/add-custom-properties-to-layer-diagrams.md)   
 [Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)   
 [Diagramas de dependencia: instrucciones](../modeling/layer-diagrams-guidelines.md)   
