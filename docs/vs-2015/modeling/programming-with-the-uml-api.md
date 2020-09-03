---
title: Programar con la API de UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, API
- UML model, extending
ms.assetid: c5937139-49d0-4439-8a9f-89f5e0474618
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bdf1111198c7f874d03596382372fe25851e37d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852127"
---
# <a name="programming-with-the-uml-api"></a>Programar con la API de UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La API de UML de Visual Studio permite escribir código para crear, leer y actualizar modelos y diagramas UML. Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 En los temas siguientes se describe la API, además de en las páginas de referencia de la API.

|Tema|Métodos y tipos de ejemplo que se describen|Características que se describen|
|-----------|-----------------------------------------|------------------------|
|[Navegar por las relaciones con la API de UML](../modeling/navigate-relationships-with-the-uml-api.md)|Elementos UML, así como sus propiedades y asociaciones. Por ejemplo, IElement y sus descendientes, incluidos: IClass, IActivity, IUseCase, IComponent, IInteraction, IModel, IPackage|En Visual Studio, los modelos UML se ajustan a la especificación de UML versión 2.1.2, que se puede obtener en la [Página de recursos de UML](https://www.uml.org/). Cada tipo es una interfaz que tiene el mismo nombre que el tipo UML precedido del prefijo "I".|
|[Crear elementos y relaciones en modelos UML](../modeling/create-elements-and-relationships-in-uml-models.md)|IPackage.CreateClass()<br /><br /> IClass.CreateOperation()|Cada tipo de elemento contiene métodos para crear sus elementos secundarios.|
|[Mostrar un modelo UML en diagramas](../modeling/display-a-uml-model-on-diagrams.md)|IShape, IDiagram<br /><br /> IShape.Move()|Cada elemento de un modelo se puede representar como una forma en un diagrama. En algunos casos, se pueden crear nuevas formas para cada objeto. Se puede cambiar la posición, el tamaño y el color de estas formas. También pueden contraerse y expandirse.|
|[Navegar por el modelo UML](../modeling/navigate-the-uml-model.md)|IModelStore<br /><br /> IDiagramContext|El modelo se guarda en el almacén de modelos.<br /><br /> El contexto del diagrama proporciona acceso al diagrama y al almacén actuales.|
|[Vincular actualizaciones del modelo UML mediante transacciones](../modeling/link-uml-model-updates-by-using-transactions.md)|ILinkedUndoContext|Puede vincular una serie de cambios a una transacción.|
|[Definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|IMenuCommand<br /><br /> IGestureExtension<br /><br /> ICommandExtension|Para extender la funcionalidad de un diagrama, puede definir comandos que se invoquen haciendo doble clic en ellos y arrastrándolos hasta el diagrama.|
|[Definir restricciones de validación para modelos UML](../modeling/define-validation-constraints-for-uml-models.md)|ValidationContext|Puede definir reglas de validación que le ayuden a asegurarse de que un modelo se ajusta a las restricciones especificadas.|
|[Obtener elementos del modelo UML a partir de IDataObject](../modeling/get-uml-model-elements-from-idataobject.md)|IElement, IShape|Cuando un elemento se arrastra desde el Explorador de modelos UML o un diagrama de UML hasta otro diagrama o aplicación, se serializa como IDataObject.|
|[Modificar diagramas de secuencia UML mediante la API de UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)|IInteraction, ILifeline, IMessage|La creación y actualización de un diagrama de interacciones es ligeramente distinta que en otros tipos de diagramas.|
|[Ampliar diagramas de capas](../modeling/extend-layer-diagrams.md)|ILayer, ILayerDiagram|Puede escribir código para crear y modificar los diagramas de capas y también validar código de programa con ellos.|

## <a name="about-the-implementation"></a>Acerca de la implementación
 Las herramientas de modelado UML se basan en [!INCLUDE[dsl](../includes/dsl-md.md)]. Un modelo de [!INCLUDE[dsl](../includes/dsl-md.md)] representa cada diagrama y paquete, y una colección de reglas y otros métodos mantiene la coherencia entre ellos.

 Los tipos de esa plataforma están visibles en algunos de los ensamblados a los que se hace referencia para escribir extensiones UML. Aunque puede crear extensiones a las herramientas UML teniendo acceso a la API de [!INCLUDE[dsl](../includes/dsl-md.md)], debería tener en cuenta las siguientes consideraciones:

- Podría encontrar que algunos cambios aparentemente simples presentan inconsistencias y efectos inesperados.

- La implementación puede cambiar en el futuro, de modo que las adaptaciones que realice utilizando la API de [!INCLUDE[dsl](../includes/dsl-md.md)] podrían dejar de funcionar.

## <a name="the-api-assemblies"></a>Los ensamblados de la API
 En esta tabla se resumen los ensamblados que proporcionan extensibilidad a las herramientas UML y los espacios de nombres que se recomienda utilizar.

|Ensamblado|Espacios de nombres|Proporciona acceso a:|
|--------------|----------------|-------------------------|
|Microsoft.VisualStudio.Uml.Interfaces|(Todo)|Los tipos UML.|
|Microsoft.VisualStudio.ArchitectureTools.Extensibility|Microsoft. VisualStudio. ArchitectureTools. Extensibility. UML|[Métodos de creación](../modeling/create-elements-and-relationships-in-uml-models.md)|
||Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation|[Diagramas y formas](../modeling/display-a-uml-model-on-diagrams.md)|
||Microsoft.VisualStudio.ArchitectureTools.Extensibility|[El proyecto de modelado](../modeling/read-a-uml-model-in-program-code.md)|
|Microsoft.VisualStudio.Modeling.Sdk.[versión]|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement>|[Extensión de comando de menú](../modeling/define-a-menu-command-on-a-modeling-diagram.md).<br /><br /> [Transacciones de deshacer vinculadas](../modeling/link-uml-model-updates-by-using-transactions.md).|
||<xref:Microsoft.VisualStudio.Modeling.Validation>|[Validación](../modeling/define-validation-constraints-for-uml-models.md)|
||(otros espacios de nombres)|Solo se recomienda para el uso avanzado.|
|Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[versión]|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement>|[Controladores de gestos](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).|
||(otros espacios de nombres)|Solo se recomienda para el uso avanzado.|
|Microsoft.VisualStudio.TeamFoundation.WorkItemTracking|Microsoft.VisualStudio.TeamFoundation.WorkItemTracking|[Vínculos a elementos de trabajo](../modeling/define-a-work-item-link-handler.md).|
|Microsoft.TeamFoundation.WorkItemTracking.Client|Microsoft.TeamFoundation.WorkItemTracking.Client|[Elementos de trabajo y sus campos](../modeling/define-a-work-item-link-handler.md).|
|Microsoft.TeamFoundation.Client|Microsoft.TeamFoundation.Client|[Elementos de trabajo y sus campos](../modeling/define-a-work-item-link-handler.md).|
|System.ComponentModel.Composition|<xref:System.ComponentModel.Composition>|[Exportación e importación para componentes MEF](../modeling/define-and-install-a-modeling-extension.md)|
|System.Linq|<xref:System.Linq>|[Manipulación sencilla de las colecciones, especialmente cuando se trabaja con relaciones](../modeling/navigate-relationships-with-the-uml-api.md).|

## <a name="see-also"></a>Consulte también
 [Ampliar modelos y diagramas UML](../modeling/extend-uml-models-and-diagrams.md) [referencia de la API para la extensibilidad del modelado UML](../modeling/api-reference-for-uml-modeling-extensibility.md)
