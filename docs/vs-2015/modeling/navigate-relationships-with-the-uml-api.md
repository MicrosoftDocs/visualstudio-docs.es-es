---
title: Navegar por las relaciones con la API de UML | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API
ms.assetid: a4d11d45-b8c0-40f9-a597-363f07659610
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0f8d1392bebf4d2591bbd7e4dc7bd8755c09f2c2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51740537"
---
# <a name="navigate-relationships-with-the-uml-api"></a>Navegar por las relaciones con la API de UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un modelo se compone de elementos vinculados entre sí mediante diferentes tipos de relaciones. En este tema se describe cómo navegar por el modelo en código de programa.  
  
## <a name="traversing-relationships"></a>Recorrer relaciones  
  
### <a name="any-relationship"></a>Cualquier relación  
 Use `GetRelatedElements<T>()` para encontrar todos los elementos que están conectados a un elemento especificado. Establezca `T` en `IRelationship` para recorrer las relaciones de todo tipo, o use un tipo más específico, como `IAssociation`, para recorrer exclusivamente ese tipo.  
  
```  
IElement anElement;  
// Select all elements related to anElement.  
Context.CurrentDiagram.SelectShapes (  
   anElement.GetRelatedElements<IRelationship>()  
    .SelectMany(e=>e.Shapes()).ToArray());  
  
```  
  
 Use `GetRelatedLinks<T>()` para buscar todas las relaciones conectadas a un elemento.  
  
```  
// Process all relationships connected to an element.  
foreach (IRelationship relationship in   
   anElement.GetRelatedLinks<IRelationship>())  
{  
  Debug.Assert(relationship.SourceElement == anElement  
      || relationship.TargetElement == anElement);  
}  
  
```  
  
### <a name="association"></a>Asociación  
 Una asociación es una relación entre dos propiedades, cada una de las cuales pertenece a un clasificador.  
  
```  
IClassifier classifier; // class, interface, component, actor, ...  
// Get all the associations sourced from this classifier  
foreach (IProperty p in classifier.GetOutgoingAssociationEnds())  
{  
  // p represents the end further end of an association.  
  IType oppositeElement = p.Type;   
    // The type to which this association connects classifier  
  
  IProperty oppositeProperty = p.Opposite;  
    // The nearer end of the association.  
  Debug.Assert(oppositeProperty.Type == classifier);  
  IAssociation association = p.Association;  
  Debug.Assert(association.MemberEnds.Contains(p)  
     && association.MemberEnds.Contains(oppositeProperty));  
}  
```  
  
### <a name="generalization-and-realization"></a>Generalización y realización  
 Acceso a extremos opuestos de la generalización:  
  
```  
foreach (IClassifier supertype in classifier.Generals) {…}  
foreach (IClassifier subtype in classifier.GetSpecifics()) {…}  
Access the relationship itself:  
foreach (IGeneralization gen in classifier.Generalizations)   
{ Debug.Assert(classifier == gen.Specific); }  
```  
  
```  
  
/// InterfaceRealization:  
IEnumerable<IInterface> GetRealizedInterfaces  
    (this IBehavioredClassifier classifier);  
IEnumerable<IBehavioredClassifier> GetRealizingClassifiers  
    (this IInterface interface);  
  
```  
  
### <a name="dependency"></a>Dependencia  
  
```  
/// Returns the elements depending on this element  
IEnumerable<INamedElement> GetDependencyClients(this INamedElement element);   
/// Returns the elements this element depends on  
IEnumerable<INamedElement> INamedElement GetDependencySuppliers(this INamedElement element);  
  
```  
  
### <a name="activity-edge"></a>Perímetro de actividad  
  
```  
/// Returns the nodes targeted by edges outgoing from this one  
IEnumerable<IActivityNode> GetActivityEdgeTargets(this IActivityNode node);  
/// Returns the nodes sourcing edges incoming to this one  
IEnumerable<IActivityNode> GetActivityEdgeSources(this IActivityNode node);  
  
```  
  
### <a name="connector-assembly-and-delegation"></a>Conector (ensamblado y delegación)  
  
```  
/// Returns the elements connected via assembly   
/// or delegation to this one  
IEnumerable<IConnectableElement> GetConnectedElements(this IConnectableElement element);  
  
```  
  
### <a name="messages-and-lifelines"></a>Mensajes y líneas de vida  
  
```  
IEnumerable<IMessage> GetAllOutgoingMessages(this ILifeline  lifeline);   
// both from lifeline and execution occurrences  
IEnumerable<IMessage> GetAllIncomingMessages(this ILifeline  lifeline);  
ILifeline GetSourceLifeline(this IMessage message);   
    // may return null for found messages  
ILifeline GetTargetLifeline(this IMessage message);    
    // may return null for lost messages  
  
```  
  
### <a name="package-import"></a>Importación de paquete  
  
```  
IEnumerable<IPackage>GetImportedPackages(this INamespace namespace);  
IEnumerable<INamespace> GetImportingNamespaces(this IPackage package);  
  
```  
  
### <a name="use-case-extend-and-include"></a>Ampliación e inclusión de casos de uso  
  
```  
IEnumerable<IUseCase>GetExtendedCases(this IUseCase usecase);  
IEnumerable<IUseCase>GetExtendingCases(this IUseCase usecase);  
IEnumerable<IUseCase>GetIncludedCases(this IUseCase usecase);  
IEnumerable<IUseCase>GetIncludingCases(this IUseCase usecase);  
```  
  
## <a name="enumerating-relationships"></a>Enumeración de relaciones  
 Todas las propiedades del modelo UML que devuelven varios valores se ajustan a la interfaz IEnumerable <>. Esto significa que puede usar [expresiones de consulta Linq](http://go.microsoft.com/fwlink/?LinkId=168834) y los métodos de extensión definidos en el **System.Linq** espacio de nombres.  
  
 Por ejemplo:  
  
```  
from shape in     Context.CurrentDiagram.GetSelectedShapes<IClassifier>()  
where shape.Color == System.Drawing.Color.Red  
select shape.Element  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Ampliar modelos y diagramas UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Navegar por el modelo UML](../modeling/navigate-the-uml-model.md)



