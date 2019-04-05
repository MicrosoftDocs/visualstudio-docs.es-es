---
title: Navegar por el modelo UML | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: 6d789b6d-2aa9-4ceb-92c4-84a300065a76
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 678c09cca8f7b90c9be6dc2b7101ca04d9f94812
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995599"
---
# <a name="navigate-the-uml-model"></a>Navegar por el modelo UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se presentan los principales tipos del modelo UML.  
  
## <a name="the-model-elements-model-and-model-store"></a>Modelo, elementos del modelo y almacén de modelos  
 Los tipos definidos en el ensamblado **Microsoft.VisualStudio.Uml.Interfaces.dll** corresponden a los tipos definidos en el [especificación de UML, versión 2.1.2](http://www.omg.org/spec/UML/2.1.2/Superstructure/PDF/).  
  
 Los tipos de la especificación de UML se realizan como interfaces en Visual Studio. La letra 'I' se antepone al nombre de cada tipo. Por ejemplo: <xref:Microsoft.VisualStudio.Uml.Classes.IElement>, <xref:Microsoft.VisualStudio.Uml.Classes.IClass>, <xref:Microsoft.VisualStudio.Uml.Interactions.IInteraction>, <xref:Microsoft.VisualStudio.Uml.Classes.IOperation>.  
  
 Todos los tipos excepto IElement heredan las propiedades de uno o varios supertipos.  
  
-   Para obtener un resumen de los tipos de modelo, vea [tipos de elemento de modelo UML](../modeling/uml-model-element-types.md).  
  
-   Para obtener detalles completos de la API, consulte [referencia de API de extensibilidad del modelado UML](../modeling/api-reference-for-uml-modeling-extensibility.md).  
  
### <a name="relationships"></a>Relaciones  
 Las propiedades y relaciones que se definen en la especificación de UML se implementan como propiedades .NET.  
  
 En la mayoría de las relaciones, la navegación puede hacerse en ambas direcciones. Una relación se corresponde con un par de propiedades, con una única propiedad del tipo en cada extremo. Por ejemplo, las propiedades `IElement.Owner` e `IElement.OwnedElements` representan dos extremos de una relación. Por tanto, esta expresión siempre se evaluará como true:  
  
 `IElement c; ...  c.OwnedElements.All(x => x.Owner == c)`  
  
 Muchas relaciones, como IAssociation, también se representan mediante un objeto que puede tener sus propias propiedades.  
  
 Si elimina un elemento del modelo, se elimina automáticamente cualquier relación de la que forme parte y se actualiza la propiedad situada en el otro extremo.  
  
 Si la especificación de UML asigna una multiplicidad de 0..1 a una propiedad, puede tener el valor `null`. Una multiplicidad con un valor máximo mayor que 1 significa que la propiedad .NET tiene el tipo: `IEnumerable<`*Tipo*`>`.  
  
 Para obtener más información sobre cómo atravesar relaciones, vea [navegar por las relaciones con la API de UML](../modeling/navigate-relationships-with-the-uml-api.md).  
  
### <a name="the-ownership-tree"></a>Árbol de propiedad  
 Un modelo contiene un árbol de objetos <xref:Microsoft.VisualStudio.Uml.Classes.IElement>. Cada elemento tiene las propiedades `OwnedElements` y `Owner`.  
  
 En la mayoría de los casos, también existen referencias a los destinos de las propiedades `Owner` y `OwnedElements` en otras propiedades que tienen nombres más específicos. Por ejemplo, cada una de las operaciones de UML pertenece a una clase UML. Por lo tanto, <xref:Microsoft.VisualStudio.Uml.Classes.IOperation> tiene una propiedad denominada <xref:Microsoft.VisualStudio.Uml.Classes.IOperation.Class%2A>, y en cada objeto <xref:Microsoft.VisualStudio.Uml.Classes.IOperation>, `Class == Owner`.  
  
 El elemento del nivel superior del árbol, que no tiene propietario, es un <xref:Microsoft.VisualStudio.Uml.AuxiliaryConstructs.IModel>. El objeto IModel está incluido en un objeto <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore>, donde es la propiedad <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore.Root%2A>.  
  
 Cada elemento del modelo se crea con un propietario. Para obtener más información, consulte [crear elementos y relaciones en modelos UML](../modeling/create-elements-and-relationships-in-uml-models.md).  
  
 ![Diagrama de clases: Modelo, diagrama, forma y elemento](../modeling/media/uml-mm1.png "UML_MM1")  
  
## <a name="shapes-and-diagrams"></a>Formas y diagramas  
 Los elementos del modelo UML se pueden representar en diagramas. Pueden aparecer diferentes subtipos de IElement en distintos tipos de diagramas.  
  
 En algunos casos, un elemento puede aparecer en varios diagramas. Por ejemplo, un elemento IUseCase puede tener varios objetos IShapes, que pueden aparecer en un único diagrama o en varios diagramas diferentes.  
  
 Las formas están organizadas en un árbol. Los bordes del árbol se representan mediante las propiedades ParentShape y ChildShapes. Los diagramas son las únicas formas que no tienen elementos primarios. Las formas de la superficie de un diagrama se crean a partir de elementos más pequeños. Por ejemplo, la forma de una clase tiene compartimientos para los atributos y las operaciones.  
  
 Para obtener más información acerca de las formas, vea [mostrar un modelo UML en diagramas](../modeling/display-a-uml-model-on-diagrams.md).  
  
## <a name="access-to-the-model-in-extensions"></a>Acceso al modelo en las extensiones  
 En las extensiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] definidas como componentes MEF, puede declarar propiedades que importen información a partir del contexto en el que se ejecuta la extensión.  
  
|Tipo de atributo|Objeto al que proporciona acceso|Más información|  
|--------------------|----------------------------------|----------------------|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation<br /><br /> .IDiagramContext<br /><br /> (en Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll)|Diagrama que tiene el foco en la actualidad.|[Definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|  
|Microsoft.VisualStudio.Modeling.ExtensionEnablement<br /><br /> .ILinkedUndoContext<br /><br /> (en Microsoft.VisualStudio.Modeling.Sdk.[version].dll)|Permite agrupar cambios en transacciones.|[Vincular actualizaciones del modelo UML mediante transacciones](../modeling/link-uml-model-updates-by-using-transactions.md)|  
|Microsoft.VisualStudio.Shell .SVsServiceProvider<br /><br /> (en Microsoft.VisualStudio.Shell.Immutable.[version].dll)|Ejecución de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que constituye el host. Desde allí se puede obtener acceso a los archivos, proyectos y otros aspectos.|[Abrir un modelo UML mediante la API de Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)|  
  
### <a name="to-get-the-context"></a>Para obtener el contexto  
 Declare una o las dos interfaces siguientes en la clase de la extensión:  
  
```  
[Import] public IDiagramContext DiagramContext { get; set; }  
  
```  
  
 Managed Extensibility Framework (MEF) establecerá enlaces entre las interfaces y las definiciones a partir de las cuales podrá obtener el diagrama actual, el almacén del modelo, el objeto raíz, etc.  
  
```  
IDiagram diagram = this.DiagramContext.CurrentDiagram;  
IClassDiagram classDiagram = diagram as IClassDiagram;  
       // or diagrams of other types  
IModelStore modelStore = diagram.ModelStore;  
IModel model = modelStore.Root;  
foreach (IDiagram diagram in modelStore.Diagrams) {...}  
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}  
```  
  
### <a name="to-get-the-current-selection"></a>Para obtener la selección actual  
  
```  
// All selected shapes and their elements  
foreach (IShape shape in diagram.SelectedShapes)  
{    
   IDiagram selectedDiagram = shape as IDiagram;  
   if (selectedDiagram != null)  
   { // no shape selected - user right-clicked the diagram  
     ... Context.CurrentDiagram ...  
   }  
   else  
   {  
     IElement selectedElement = shape.Element;  
   ...}  
// All selected shapes that display a specfic type of element  
foreach (IShape<IInterface> in   
   diagram.GetSelectedShapes<IInterface>())   
{...}  
```  
  
## <a name="accessing-another-model-or-diagrams"></a>Tener acceso a otro modelo o diagramas  
 Puede realizar lo siguiente:  
  
-   Use Model Bus de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para crear vínculos entre elementos de modelos diferentes. Para obtener más información, consulte [integrar modelos UML con otros modelos y herramientas](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
-   Cargue un proyecto y diagramas de modelado en el modo de solo lectura sin hacerlo visible en la interfaz de usuario de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Para obtener más información, consulte [leer un modelo UML en código de programa](../modeling/read-a-uml-model-in-program-code.md).  
  
-   Abra un proyecto de modelado y sus diagramas en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y, a continuación, tenga acceso al contenido. Para obtener más información, consulte [abrir un modelo UML mediante la API de Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).  
  
## <a name="see-also"></a>Vea también  
 [Ampliar modelos y diagramas UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Programar con la API de UML](../modeling/programming-with-the-uml-api.md)
