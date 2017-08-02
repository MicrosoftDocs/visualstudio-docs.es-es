---
title: "Navegar y actualizar un modelo de código de programa | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
ms.assetid: 1427ae91-be8a-4ce7-85df-00038faa2cbb
caps.latest.revision: 26
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: eb2ab9d49cdeb1ed71da8ef67841f7796862dc30
ms.openlocfilehash: f17f676025a19efb09184b7a49645986723cb29f
ms.lasthandoff: 02/22/2017

---
# <a name="navigating-and-updating-a-model-in-program-code"></a>Navegar y actualizar un modelo en el código del programa
Puede escribir código para crear y eliminar elementos del modelo, establecer sus propiedades y crear y eliminar los vínculos entre elementos. Todos los cambios deben realizarse dentro de una transacción. Si se ven los elementos en un diagrama, el diagrama se "fija" automáticamente al final de la transacción.  
  
## <a name="in-this-topic"></a>En este tema  
 [Un ejemplo de definición de DSL](#example)  
  
 [Navegar por el modelo](#navigation)  
  
 [Acceso a la información de clase](#metadata)  
  
 [Realizar cambios en una transacción](#transaction)  
  
 [Crear elementos del modelo](#elements)  
  
 [Crear vínculos de relación](#links)  
  
 [Eliminar elementos](#deleteelements)  
  
 [Eliminar vínculos de relación](#deletelinks)  
  
 [Reordenación de los vínculos de una relación](#reorder)  
  
 [Bloqueos](#locks)  
  
 [Copiar y pegar](#copy)  
  
 [Navegar y actualizar diagramas](#diagrams)  
  
 [Navegar entre las formas y elementos](#views)  
  
 [Propiedades de formas y conectores](#shapeProperties)  
  
 [DocView y DocData](#docdata)  
  
##  <a name="a-nameexamplea-an-example-dsl-definition"></a><a name="example"></a>Un ejemplo de definición de DSL  
 Esta es la parte principal de DslDefinition.dsl para los ejemplos de este tema:  
  
 ![Diagrama de definición DSL - modelo de árbol genealógico](../modeling/media/familyt_person.png "FamilyT_Person")  
  
 Este modelo es una instancia de este DSL:  
  
 ![Modelo de árbol de familia Tudor](~/docs/modeling/media/tudor_familytreemodel.png "Tudor_FamilyTreeModel")  
  
### <a name="references-and-namespaces"></a>Espacios de nombres y referencias  
 Para ejecutar el código de este tema, se debe hacer referencia:  
  
 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`  
  
 El código usará este espacio de nombres:  
  
 `using Microsoft.VisualStudio.Modeling;`  
  
 Además, si está escribiendo el código en un proyecto diferente de uno en el que se ha definido su DSL, debe importar el ensamblado que se compila el proyecto de Dsl.  
  
##  <a name="a-namenavigationa-navigating-the-model"></a><a name="navigation"></a>Navegar por el modelo  
  
### <a name="properties"></a>Propiedades  
 Propiedades del dominio que se definen en la definición de DSL se convierten en propiedades que puede tener acceso en el código de programa:  
  
 `Person henry = ...;`  
  
 `if (henry.BirthDate < 1500) ...`  
  
 `if (henry.Name.EndsWith("VIII")) ...`  
  
 Si desea establecer una propiedad, debe hacerlo dentro de un [transacciones](#transaction):  
  
 `henry.Name = "Henry VIII";`  
  
 Si está en de la definición de DSL, una propiedad **tipo** es **calculado**, no puede establecerla. Para obtener más información, consulte [calculado y las propiedades de almacenamiento personalizada](../modeling/calculated-and-custom-storage-properties.md).  
  
### <a name="relationships"></a>Relaciones  
 Relaciones de dominio que se definen en la definición de DSL se convierten en pares de propiedades, uno en la clase en cada extremo de la relación. Los nombres de las propiedades aparecen en el diagrama de DslDefinition como etiquetas en las funciones en cada lado de la relación. Dependiendo de la multiplicidad de la función, el tipo de la propiedad es la clase en el otro extremo de la relación, o bien una colección de esa clase.  
  
 `foreach (Person child in henry.Children) { ... }`  
  
 `FamilyTreeModel ftree = henry.FamilyTreeModel;`  
  
 Las propiedades en extremos opuestos de una relación siempre están recíproco. Cuando se crea o se elimina un vínculo, se actualizan las propiedades de rol en ambos elementos. La expresión siguiente (que usa las extensiones de `System.Linq`) es siempre true para la relación ParentsHaveChildren en el ejemplo:  
  
 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`  
  
 `&& p.Parents.All(parent => parent.Children.Contains(p));`  
  
 **ElementLinks**. Una relación también se representa mediante un elemento de modelo que se denomina un *vínculo*, que es una instancia del tipo de relación de dominio. Un vínculo siempre tiene elementos de un origen y un destino. El elemento de origen y el elemento de destino pueden ser el mismo.  
  
 Puede tener acceso a un vínculo y sus propiedades:  
  
 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`  
  
 `// This is now true:`  
  
 `link == null || link.Parent == henry && link.Child == edward`  
  
 De forma predeterminada, no más de una instancia de una relación puede vincular cualquier par de elementos de modelo. Pero si se encuentra en la definición de DSL, el `Allow Duplicates` indicador es true para la relación, a continuación, puede haber más de un vínculo y debe usar `GetLinks`:  
  
 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`  
  
 También existen otros métodos para tener acceso a vínculos. Por ejemplo:  
  
 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`  
  
 **Funciones ocultas.** Si se encuentra en la definición de DSL, **se genera propiedad** es **false** para un rol determinado, a continuación, no se genera propiedad que corresponde a ese rol. Sin embargo, todavía puede tener acceso a los vínculos y recorrer los vínculos con los métodos de la relación:  
  
 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`  
  
 En el ejemplo se usan con más frecuencia es la <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>relación, que incluye vínculos a la forma en que se muestra en un diagrama de un elemento de modelo:</xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>  
  
 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`  
  
### <a name="the-element-directory"></a>El directorio del elemento  
 Puede tener acceso a todos los elementos en el almacén mediante el elemento de directorio:  
  
 `store.ElementDirectory.AllElements`  
  
 También hay métodos para buscar elementos, como las siguientes:  
  
 `store.ElementDirectory.FindElements(Person.DomainClassId);`  
  
 `store.ElementDirectory.GetElement(elementId);`  
  
##  <a name="a-namemetadataa-accessing-class-information"></a><a name="metadata"></a>Acceso a la información de clase  
 Puede obtener información sobre las clases, relaciones y otros aspectos de la definición de DSL. Por ejemplo:  
  
 `DomainClassInfo personClass = henry.GetDomainClass();`  
  
 `DomainPropertyInfo birthProperty =`  
  
 `personClass.FindDomainProperty("BirthDate")`  
  
 `DomainRelationshipInfo relationship =`  
  
 `link.GetDomainRelationship();`  
  
 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`  
  
 Las clases de antecesor de elementos de modelo son las siguientes:  
  
-   ModelElement - todos los elementos y relaciones son ModelElements  
  
-   ElementLink - todas las relaciones son ElementLinks  
  
##  <a name="a-nametransactiona-perform-changes-inside-a-transaction"></a><a name="transaction"></a>Realizar cambios en una transacción  
 Siempre que el código de programa cambia nada en el almacén, debe hacerlo dentro de una transacción. Esto se aplica a todos los elementos del modelo, las relaciones, formas, diagramas y sus propiedades. Para obtener más información, consulte <xref:Microsoft.VisualStudio.Modeling.Transaction>.</xref:Microsoft.VisualStudio.Modeling.Transaction>  
  
 Es el método más conveniente para administrar una transacción con un `using` instrucción dentro de un `try...catch` instrucción:  
  
```  
Store store; ...  
try  
{  
  using (Transaction transaction =  
    store.TransactionManager.BeginTransaction("update model"))  
    // Outermost transaction must always have a name.  
  {  
    // Make several changes in Store:  
    Person p = new Person(store);  
    p.FamilyTreeModel = familyTree;  
    p.Name = "Edward VI";  
    // end of changes to Store  
  
    transaction.Commit(); // Don't forget this!  
  } // transaction disposed here  
}  
catch (Exception ex)  
{  
  // If an exception occurs, the Store will be   
  // rolled back to its previous state.  
}  
```  
  
 Puede realizar cualquier número de cambios dentro de una transacción. Puede abrir las nuevas transacciones dentro de una transacción activa.  
  
 Para que los cambios sean permanentes, debe `Commit` la transacción antes de eliminarlo. Si se produce una excepción que no se detecta en la transacción, el almacén se restablecerá a su estado antes de los cambios.  
  
##  <a name="a-nameelementsa-creating-model-elements"></a><a name="elements"></a>Crear elementos del modelo  
 En este ejemplo se agrega un elemento a un modelo existente:  
  
```  
FamilyTreeModel familyTree = ...; // The root of the model.         
using (Transaction t =  
    familyTree.Store.TransactionManager  
    .BeginTransaction("update model"))  
{  
  // Create a new model element   
  // in the same partition as the model root:  
  Person edward = new Person(familyTree.Partition);  
  // Set its embedding relationship:  
  edward.FamilyTreeModel = familyTree;  
          // same as: familyTree.People.Add(edward);  
  // Set its properties:  
  edward.Name = "Edward VII";  
  t.Commit(); // Don't forget this!  
}  
```  
  
 Este ejemplo ilustra estos puntos esenciales sobre la creación de un elemento:  
  
-   Crear el nuevo elemento en una partición específica de la tienda. Para los elementos del modelo y las relaciones, pero no formas, suele ser la partición predeterminada.  
  
-   Facilitan el destino de una relación de incrustación. En la DslDefinition de este ejemplo, cada persona debe ser el destino de la relación FamilyTreeHasPeople de incrustación. Para lograr esto, nos podemos establecer la propiedad de la función FamilyTreeModel del objeto Person o agregar a la persona a la propiedad de la función de personas del objeto FamilyTreeModel.  
  
-   Establecer las propiedades de un nuevo elemento, especialmente la propiedad para la que `IsName` es true en la DslDefinition. Este indicador marca la propiedad que sirve para identificar el elemento de forma única dentro de su propietario. En este caso, la propiedad Name tiene esa marca.  
  
-   La definición de DSL de este DSL debe cargada en el almacén. Si está escribiendo una extensión como un comando de menú, normalmente será ya es true. En otros casos, puede cargar el modelo en el almacén, o explícitamente utilice <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus>para la carga.</xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus> Para obtener más información, consulte [Cómo: abrir un modelo del archivo de código de programa](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
 Cuando se crea un elemento de esta forma, automáticamente se crea una forma (si el DSL tiene un diagrama). Aparece en una ubicación asignada automáticamente, con la forma predeterminada, el color y otras características. Si desea controlar dónde y cómo aparece la forma asociada, consulte [creación de un elemento y su forma](#merge).  
  
##  <a name="a-namelinksa-creating-relationship-links"></a><a name="links"></a>Crear vínculos de relación  
 Hay dos relaciones definidas en la definición de DSL de ejemplo. Cada relación define un *propiedad función* en la clase en cada extremo de la relación.  
  
 Hay tres formas en que puede crear una instancia de una relación. Cada uno de estos tres métodos tiene el mismo efecto:  
  
-   Establezca la propiedad del Reproductor del rol de origen. Por ejemplo:  
  
    -   `familyTree.People.Add(edward);`  
  
    -   `edward.Parents.Add(henry);`  
  
-   Establezca la propiedad del Reproductor de rol de destino. Por ejemplo:  
  
    -   `edward.familyTreeModel = familyTree;`  
  
         La multiplicidad de este rol es `1..1`, por lo que asignamos el valor.  
  
    -   `henry.Children.Add(edward);`  
  
         La multiplicidad de este rol es `0..*`, por lo que agregamos a la colección.  
  
-   Construir explícitamente una instancia de la relación. Por ejemplo:  
  
    -   `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`  
  
    -   `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`  
  
 El último método es útil si desea establecer las propiedades de la relación propiamente dicha.  
  
 Cuando se crea un elemento de esta forma, se crea automáticamente un conector en el diagrama, pero tiene una forma predeterminada, el color y otras características. Para controlar cómo se crea el conector asociado, vea [creación de un elemento y su forma](#merge).  
  
##  <a name="a-namedeleteelementsa-deleting-elements"></a><a name="deleteelements"></a>Eliminar elementos  
 Eliminar un elemento mediante una llamada a `Delete()`:  
  
 `henry.Delete();`  
  
 Esta operación eliminará también:  
  
-   Vínculos de relación hacia y desde el elemento. Por ejemplo, `edward.Parents` ya no contendrá `henry`.  
  
-   Elementos en roles para los que el `PropagatesDelete` indicador es true. Por ejemplo, se eliminarán la forma que muestra el elemento.  
  
 De forma predeterminada, cada relación de incrustación tiene `PropagatesDelete` verdadera en el rol de destino. Eliminar `henry` no elimina el `familyTree`, pero `familyTree.Delete()` tendría que eliminar todo el `Persons`. Para obtener más información, consulte [personalización del comportamiento de eliminación](../modeling/customizing-deletion-behavior.md).  
  
 De forma predeterminada, `PropagatesDelete` no es cierto para los roles de relaciones de referencia.  
  
 Puede hacer que las reglas de eliminación omitir propagaciones específicos cuando se elimina un objeto. Esto resulta útil si sustituye un elemento de otro. Proporcionar el GUID de uno o varios roles para los que no se propagan eliminación. Puede obtener el GUID de la clase de relación:  
  
 `henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`  
  
 (Este ejemplo concreto no tendría ningún efecto, porque `PropagatesDelete` es `false` para los roles de la `ParentsHaveChildren` relación.)  
  
 En algunos casos, se impedirá la eliminación por la existencia de un bloqueo, en el elemento o en un elemento que eliminaría la propagación. Puede usar `element.CanDelete()` para comprobar si se puede eliminar el elemento.  
  
##  <a name="a-namedeletelinksa-deleting-relationship-links"></a><a name="deletelinks"></a>Eliminar vínculos de relación  
 Puede eliminar un vínculo de relación mediante la eliminación de un elemento de una propiedad de rol:  
  
 `henry.Children.Remove(edward); // or:`  
  
 `edward.Parents.Remove(henry);  // or:`  
  
 También puede eliminar el vínculo explícitamente:  
  
 `edwardHenryLink.Delete();`  
  
 Estos tres métodos que todos tienen el mismo efecto. Sólo debe usar uno de ellos.  
  
 Si la función tiene la multiplicidad de 0.. 1 o 1.. 1, puede establecer en `null`, o a otro valor:  
  
 `edward.FamilyTreeModel = null;`o:  
  
 `edward.FamilyTreeModel = anotherFamilyTree;`  
  
##  <a name="a-namereordera-re-ordering-the-links-of-a-relationship"></a><a name="reorder"></a>Volver a ordenar los vínculos de una relación  
 Los vínculos de una relación determinada que se obtienen o dirigido a un elemento de modelo determinado tienen una secuencia concreta. Aparecen en el orden en que se agregaron. Por ejemplo, esta instrucción siempre dará a los elementos secundarios en el mismo orden:  
  
 `foreach (Person child in henry.Children) ...`  
  
 Puede cambiar el orden de los vínculos:  
  
 `ParentsHaveChildren link = GetLink(henry,edward);`  
  
 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`  
  
 `DomainRoleInfo role =`  
  
 `link.GetDomainRelationship().DomainRoles[0];`  
  
 `link.MoveBefore(role, nextLink);`  
  
##  <a name="a-namelocksa-locks"></a><a name="locks"></a>Bloqueos  
 Los cambios pueden evitarse con un bloqueo. Los bloqueos se pueden establecer en elementos individuales, en particiones y en el almacén. Si alguno de estos niveles tiene un bloqueo que evita que el tipo de cambio que desea realizar, podría producirá una excepción cuando se intente. Puede detectar si los bloqueos se establecen mediante el elemento. GetLocks(), que es un método de extensión que se define en el espacio de nombres <xref:Microsoft.VisualStudio.Modeling.Immutability>.</xref:Microsoft.VisualStudio.Modeling.Immutability>  
  
 Para obtener más información, consulte [definir una directiva de bloqueo para crear segmentos de sólo lectura](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).  
  
##  <a name="a-namecopya-copy-and-paste"></a><a name="copy"></a>Copiar y pegar  
 Puede copiar elementos o grupos de elementos en una <xref:System.Windows.Forms.IDataObject>:</xref:System.Windows.Forms.IDataObject>  
  
```  
Person person = personShape.ModelElement as Person;  
Person adopter = adopterShape.ModelElement as Person;  
IDataObject data = new DataObject();  
personShape.Diagram.ElementOperations  
      .Copy(data, person.Children.ToList<ModelElement>());  
```  
  
 Los elementos se almacenan como un grupo de elementos serializados.  
  
 Puede combinar elementos de IDataObject en un modelo:  
  
```  
using (Transaction t = targetDiagram.Store.  
        TransactionManager.BeginTransaction("paste"))  
{  
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);  
}  
```  
  
 `Merge ()`puede aceptar cualquiera una `PresentationElement` o `ModelElement`. Si se le asigna un `PresentationElement`, también puede especificar una posición en el diagrama de destino como tercer parámetro.  
  
##  <a name="a-namediagramsa-navigating-and-updating-diagrams"></a><a name="diagrams"></a>Navegar y actualizar diagramas  
 En un DSL, el elemento de modelo de dominio, que representa un concepto como persona o una canción, es independiente del elemento de forma que representa lo que ve en el diagrama. El elemento de modelo de dominio almacena las propiedades importantes y las relaciones de los conceptos. El elemento de forma almacena el tamaño, posición y color de la vista del objeto en el diagrama y el diseño de sus componentes.  
  
### <a name="presentation-elements"></a>Elementos de presentación  
 ![Diagrama de clases de tipos de forma y elemento base](../modeling/media/dslshapesandelements.png "DSLshapesAndElements")  
  
 En la definición de DSL, cada elemento que especifique crea una clase que se deriva de una de las siguientes clases estándares.  
  
|Tipo de elemento|Clase base|  
|---------------------|----------------|  
|Clase de dominio|<xref:Microsoft.VisualStudio.Modeling.ModelElement></xref:Microsoft.VisualStudio.Modeling.ModelElement>|  
|Relación de dominio|<xref:Microsoft.VisualStudio.Modeling.ElementLink></xref:Microsoft.VisualStudio.Modeling.ElementLink>|  
|Forma|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape></xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|  
|Conector|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape></xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|  
|Diagram|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram></xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|  
  
 Normalmente, un elemento en un diagrama representa un elemento de modelo. Normalmente (pero no siempre), un <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>representa una instancia de la clase de dominio y un <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>representa una instancia de la relación de dominio.</xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> </xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> El <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>relación vincula una forma de nodo o vínculo al elemento de modelo que representa.</xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>  
  
 Cada nodo o vínculo forma pertenece a un diagrama. Una forma de vínculo binario conecta dos formas de nodo.  
  
 Formas pueden tener formas secundarias en dos conjuntos. Una forma en la `NestedChildShapes` conjunto se limita al cuadro de límite de su elemento primario. Una forma en la `RelativeChildShapes` lista puede aparecer fuera o parcialmente fuera de los límites del elemento primario: por ejemplo, una etiqueta o un puerto. Un diagrama no tiene ningún `RelativeChildShapes` y no `Parent`.  
  
###  <a name="a-nameviewsa-navigating-between-shapes-and-elements"></a><a name="views"></a>Navegar entre las formas y elementos  
 Elementos del modelo de dominio y los elementos de forma que se relacionan mediante la <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>relación.</xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>  
  
```c#  
// using Microsoft.VisualStudio.Modeling;  
// using Microsoft.VisualStudio.Modeling.Diagrams;  
// using System.Linq;  
Person henry = ...;  
PersonShape henryShape =   
  PresentationViewsSubject.GetPresentation(henry)  
    .FirstOrDefault() as PersonShape;  
```  
  
 La misma relación incluye vínculos a los conectores en el diagrama de relaciones:  
  
```  
Descendants link = Descendants.GetLink(henry, edward);  
DescendantConnector dc =  
   PresentationViewsSubject.GetPresentation(link)  
     .FirstOrDefault() as DescendantConnector;  
// dc.FromShape == henryShape && dc.ToShape == edwardShape  
```  
  
 Esta relación también incluye vínculos a la raíz del modelo al diagrama:  
  
```  
FamilyTreeDiagram diagram =   
   PresentationViewsSubject.GetPresentation(familyTree)  
      .FirstOrDefault() as FamilyTreeDiagram;  
```  
  
 Para obtener el elemento de modelo representado por una forma, use:  
  
 `henryShape.ModelElement as Person`  
  
 `diagram.ModelElement as FamilyTreeModel`  
  
### <a name="navigating-around-the-diagram"></a>Desplazarse por el diagrama  
 En general no es recomendable para navegar entre las formas y conectores del diagrama. Es mejor navegar por las relaciones en el modelo, moverse entre las formas y conectores sólo cuando es necesario trabajar en el aspecto del diagrama. Estos métodos vínculo conectores a las formas en cada extremo:  
  
 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`  
  
 `connector.FromShape, connector.ToShape`  
  
 Muchas de las formas están compuestos; se compone de una forma principal y una o varias capas de elementos secundarios. Se dice que las formas que se sitúan en relación con otra forma su *niños*. Cuando se mueve la forma primaria, los elementos secundarios se mueven con él.  
  
 *Elementos secundarios relativos* puede aparecer fuera del cuadro de límite de la forma principal. *Anidar* hijos estrictamente aparecen dentro de los límites del elemento primario.  
  
 Para obtener el conjunto superior de formas en un diagrama, use:  
  
 `Diagram.NestedChildShapes`  
  
 Las clases de antecesor de formas y conectores son:  
  
 <xref:Microsoft.VisualStudio.Modeling.ModelElement></xref:Microsoft.VisualStudio.Modeling.ModelElement>  
  
 --<xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement></xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>  
  
 --<xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement></xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>  
  
 -----<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape></xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>  
  
 -------<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram></xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>  
  
 ------- *YourShape*  
  
 -----<xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape></xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>  
  
 -------<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape></xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>  
  
 --------- *YourConnector*  
  
###  <a name="a-nameshapepropertiesa-properties-of-shapes-and-connectors"></a><a name="shapeProperties"></a>Propiedades de formas y conectores  
 En la mayoría de los casos, no es necesario realizar cambios explícitos en las formas. Cuando se han cambiado los elementos del modelo, las reglas de "arreglar" actualización las formas y conectores. Para obtener más información, consulte [responder a y propagar los cambios](../modeling/responding-to-and-propagating-changes.md).  
  
 Sin embargo, resulta útil realizar algunos cambios explícitas a las formas en las propiedades que son independientes de los elementos del modelo. Por ejemplo, puede cambiar estas propiedades:  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A>-Determina el alto y ancho de la forma.</xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A>  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A>-posición con respecto a la forma principal o diagrama</xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A>  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A>-el conjunto de lápices y pinceles usados para dibujar la forma o conector</xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A>  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A>-hace que la forma sea invisible</xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A>  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A>-hace que la forma esté visible después de un`Hide()`</xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A>  
  
###  <a name="a-namemergea-creating-an-element-and-its-shape"></a><a name="merge"></a>Creación de un elemento y su forma  
 Al crear un elemento y vincularla al árbol de relaciones de incrustación, una forma se crea automáticamente y asociada a él. Para ello, las reglas de "reparación" que se ejecutan al final de la transacción. Sin embargo, la forma aparecerá en una ubicación que se asigna automáticamente y su forma, color y otras características tendrán valores predeterminados. Para controlar cómo se crea la forma, puede utilizar la función de combinación. Debe agregar primero los elementos que desea agregar en una ElementGroup y luego combinar el grupo en el diagrama.  
  
 Este método:  
  
-   Establece el nombre, si ha asignado una propiedad como el nombre del elemento.  
  
-   Respeta las directivas de mezcla de elemento especificado en la definición de DSL.  
  
 Este ejemplo crea una forma en la posición del mouse cuando el usuario hace doble clic en el diagrama. En la definición de DSL para este ejemplo, el `FillColor` propiedad de `ExampleShape` ha sido expuesto.  
  
```  
  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
partial class MyDiagram  
{  
  public override void OnDoubleClick(DiagramPointEventArgs e)  
  {  
    base.OnDoubleClick(e);  
  
    using (Transaction t = this.Store.TransactionManager  
        .BeginTransaction("double click"))  
    {  
      ExampleElement element = new ExampleElement(this.Store);  
      ElementGroup group = new ElementGroup(element);  
  
      { // To use a shape of a default size and color, omit this block.  
        ExampleShape shape = new ExampleShape(this.Partition);  
        shape.ModelElement = element;  
        shape.AbsoluteBounds = new RectangleD(0, 0, 1.5, 1.0);  
        shape.FillColor = System.Drawing.Color.Azure;  
        group.Add(shape);  
      }  
  
      this.ElementOperations.MergeElementGroupPrototype(  
        this,  
        group.CreatePrototype(),  
        PointD.ToPointF(e.MousePosition));  
      t.Commit();  
    }  
  }  
}  
  
```  
  
 Si proporciona más de una forma, establezca sus posiciones relativas utilizando la `AbsoluteBounds`.  
  
 También puede establecer el color y otras propiedades expuestas de conectores con este método.  
  
### <a name="use-transactions"></a>Usar transacciones  
 Formas, conectores y diagramas son subtipos de <xref:Microsoft.VisualStudio.Modeling.ModelElement>directo en el almacén y.</xref:Microsoft.VisualStudio.Modeling.ModelElement> Por lo tanto, debe realizar cambios en ellos sólo dentro de una transacción. Para obtener más información, consulte [Cómo: usar transacciones para actualizar el modelo](../modeling/how-to-use-transactions-to-update-the-model.md).  
  
##  <a name="a-namedocdataa-document-view-and-document-data"></a><a name="docdata"></a>Vista de documento y los datos de documentos  
 ![Diagrama de clases de tipos de diagrama estándar](../modeling/media/dsldiagramsanddocs.png "DSLDiagramsandDocs")  
  
## <a name="store-partitions"></a>Almacenar particiones  
 Cuando se carga un modelo, se carga el diagrama adjunto al mismo tiempo. Normalmente, se carga el modelo en Store.DefaultPartition y se carga el contenido del diagrama en otra partición. Normalmente, el contenido de cada partición se cargan y guardan en un archivo independiente.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Modeling.ModelElement></xref:Microsoft.VisualStudio.Modeling.ModelElement>   
 [Validación en un lenguaje específico de dominio](../modeling/validation-in-a-domain-specific-language.md)   
 [Generar código a partir de un lenguaje específico de dominio](../modeling/generating-code-from-a-domain-specific-language.md)   
 [Cómo: usar transacciones para actualizar el modelo](../modeling/how-to-use-transactions-to-update-the-model.md)   
 [Integrar modelos utilizando Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Responder a los cambios y propagarlos](../modeling/responding-to-and-propagating-changes.md)

