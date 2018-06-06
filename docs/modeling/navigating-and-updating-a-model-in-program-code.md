---
title: Navegar y actualizar un modelo en el código del programa
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 18f4153db019dd6ded97337d4599f02a6b02ef49
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748939"
---
# <a name="navigate-and-update-a-model-in-program-code"></a>Navegar por un modelo en el código del programa y actualizarlo

Puede escribir código para crear y eliminar elementos del modelo, establecer sus propiedades y crear y eliminar los vínculos entre elementos. Todos los cambios deben realizarse dentro de una transacción. Si se ven los elementos en un diagrama, el diagrama se "corregirá" automáticamente al final de la transacción.

## <a name="in-this-topic"></a>En este tema
 [Un ejemplo de definición de DSL](#example)

 [Navegar por el modelo](#navigation)

 [Acceso a la información de clase](#metadata)

 [Realizar cambios en una transacción](#transaction)

 [Crear elementos del modelo](#elements)

 [Creación de vínculos de relación](#links)

 [Eliminar elementos](#deleteelements)

 [Eliminar vínculos de relación](#deletelinks)

 [Reordenación de los vínculos de una relación](#reorder)

 [Bloqueos](#locks)

 [Copiar y pegar](#copy)

 [Navegar y actualizar diagramas](#diagrams)

 [Navegar entre las formas y elementos](#views)

 [Propiedades de formas y conectores](#shapeProperties)

 [DocView y DocData](#docdata)

##  <a name="example"></a> Un ejemplo de definición de DSL
 Esta es la parte principal de DslDefinition.dsl de los ejemplos de este tema:

 ![Diagrama de definición DSL &#45; modelo de árbol genealógico](../modeling/media/familyt_person.png)

 Este modelo es una instancia de este DSL:

 ![Modelo de árbol de familia Tudor](../modeling/media/tudor_familytreemodel.png)

### <a name="references-and-namespaces"></a>Las referencias y los espacios de nombres
 Para ejecutar el código de este tema, se debe hacer referencia:

 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`

 El código usará este espacio de nombres:

 `using Microsoft.VisualStudio.Modeling;`

 Además, si está escribiendo el código en un proyecto diferente de la que en el que se define el ADSL, debe importar el ensamblado que se compila el proyecto de Dsl.

##  <a name="navigation"></a> Navegar por el modelo

### <a name="properties"></a>Propiedades
 Propiedades del dominio que definen en la definición de DSL se convierten en propiedades que se pueden tener acceso a código de programa:

 `Person henry = ...;`

 `if (henry.BirthDate < 1500) ...`

 `if (henry.Name.EndsWith("VIII")) ...`

 Si desea establecer una propiedad, debe hacerlo dentro de un [transacciones](#transaction):

 `henry.Name = "Henry VIII";`

 Si está en de la definición DSL, una propiedad **tipo** es **calculado**, no puede establecerlo. Para obtener más información, consulte [calculadas y las propiedades de almacenamiento personalizada](../modeling/calculated-and-custom-storage-properties.md).

### <a name="relationships"></a>Relaciones
 Las relaciones de dominio que definen en la definición de DSL se convierten en pares de propiedades, uno en la clase en cada extremo de la relación. Los nombres de las propiedades aparecen en el diagrama de DslDefinition como etiquetas en las funciones en cada lado de la relación. Dependiendo de la multiplicidad de la función, el tipo de la propiedad es la clase en el otro extremo de la relación, o una colección de esa clase.

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 Las propiedades en extremos opuestos de una relación siempre son recíproco. Cuando se crea o se elimina un vínculo, se actualizan las propiedades de rol en ambos elementos. La expresión siguiente (que usa las extensiones de `System.Linq`) es siempre true para la relación de ParentsHaveChildren en el ejemplo:

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **ElementLinks**. Una relación también se representa mediante un elemento de modelo que se llama a un *vínculo*, que es una instancia del tipo de relación de dominio. Un vínculo siempre tiene un origen y un destino elemento. El elemento de origen y el elemento de destino pueden ser el mismo.

 Puede tener acceso a un vínculo y sus propiedades:

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 De forma predeterminada, no más de una instancia de una relación se permite para vincular cualquier par de elementos del modelo. Pero si se encuentra en la definición DSL, el `Allow Duplicates` marca es true para la relación, a continuación, puede haber más de un vínculo y debe usar `GetLinks`:

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 También existen otros métodos para tener acceso a vínculos. Por ejemplo:

 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`

 **Funciones ocultas.** Si se encuentra en la definición DSL, **se genera de propiedad** es **false** para un rol determinado, a continuación, ninguna propiedad se genera que corresponde a ese rol. Sin embargo, todavía puede tener acceso a los vínculos y recorrer los vínculos con los métodos de la relación:

 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`

 El ejemplo de uso más frecuente es la <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relación, lo que vincula un elemento del modelo a la forma en que se muestra en un diagrama:

 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`

### <a name="the-element-directory"></a>El directorio del elemento
 Puede tener acceso a todos los elementos en el almacén mediante el directorio de elemento:

 `store.ElementDirectory.AllElements`

 También hay métodos para buscar elementos, como las siguientes:

 `store.ElementDirectory.FindElements(Person.DomainClassId);`

 `store.ElementDirectory.GetElement(elementId);`

##  <a name="metadata"></a> Acceso a la información de clase
 Puede obtener información acerca de las clases, relaciones y otros aspectos de la definición DSL. Por ejemplo:

 `DomainClassInfo personClass = henry.GetDomainClass();`

 `DomainPropertyInfo birthProperty =`

 `personClass.FindDomainProperty("BirthDate")`

 `DomainRelationshipInfo relationship =`

 `link.GetDomainRelationship();`

 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`

 Las clases de antecesores de elementos de modelo son los siguientes:

-   ModelElement - todos los elementos y las relaciones son ModelElements

-   ElementLink - todas las relaciones son ElementLinks

##  <a name="transaction"></a> Realizar cambios en una transacción
 Cada vez que el código de programa cambia nada en el almacén, debe hacerlo dentro de una transacción. Esto se aplica a todos los elementos del modelo, las relaciones, formas, diagramas y sus propiedades. Para obtener más información, consulta <xref:Microsoft.VisualStudio.Modeling.Transaction>.

 Es el método más conveniente de administrar una transacción con un `using` instrucción dentro de un `try...catch` instrucción:

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

 Puede realizar cualquier número de cambios dentro de una transacción. También puede abrir las nuevas transacciones dentro de una transacción activa.

 Para realizar los cambios permanentes, debe `Commit` la transacción antes de que se elimina. Si se produce una excepción que no se detecta en la transacción, el almacén se restablecerá a su estado antes de los cambios.

##  <a name="elements"></a> Crear elementos del modelo
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

 En este ejemplo se muestra estos puntos esenciales sobre la creación de un elemento:

-   Crear el nuevo elemento en una partición específica de la tienda. Para elementos del modelo y las relaciones, pero no formas, suele ser la partición predeterminada.

-   Conviértalo en el destino de una relación de incrustación. En la DslDefinition de este ejemplo, cada persona debe ser el destino de relación FamilyTreeHasPeople de incrustación. Para lograr esto, se puede establecer la propiedad de la función FamilyTreeModel del objeto Person o agrega a la persona a la propiedad del rol de personas del objeto FamilyTreeModel.

-   Establecer las propiedades de un elemento nuevo, especialmente la propiedad para la que `IsName` es true en la DslDefinition. Esta marca marca la propiedad que sirve para identificar el elemento de forma única dentro de su propietario. En este caso, la propiedad Name tiene dicha marca.

-   La definición DSL de este DSL debe haberse cargada en el almacén. Si está escribiendo una extensión, como un comando de menú, normalmente será ya es true. En otros casos, puede explícitamente cargar el modelo en la tienda o usar <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus> para cargar el recurso. Para obtener más información, consulte [Cómo: abrir un modelo de archivo en el código de programa](../modeling/how-to-open-a-model-from-file-in-program-code.md).

 Cuando se crea un elemento de esta manera, una forma se crea automáticamente (si DSL tiene un diagrama). Aparece en una ubicación asignada automáticamente, con forma predeterminada, el color y otras características. Si desea controlar dónde y cómo se muestra la forma asociada, vea [creación de un elemento y su forma](#merge).

##  <a name="links"></a> Creación de vínculos de relación
 Hay dos relaciones definidas en el ejemplo de definición DSL. Cada relación define un *propiedad role* en la clase en cada extremo de la relación.

 Hay tres formas en que puede crear una instancia de una relación. Cada uno de estos tres métodos tiene el mismo efecto:

-   Establezca la propiedad del Reproductor de rol de origen. Por ejemplo:

    -   `familyTree.People.Add(edward);`

    -   `edward.Parents.Add(henry);`

-   Establezca la propiedad del Reproductor de rol de destino. Por ejemplo:

    -   `edward.familyTreeModel = familyTree;`

         La multiplicidad de este rol es `1..1`, por lo que se asigna el valor.

    -   `henry.Children.Add(edward);`

         La multiplicidad de este rol es `0..*`, por lo que agregamos a la colección.

-   Construir una instancia de la relación de forma explícita. Por ejemplo:

    -   `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`

    -   `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`

 El último método es útil si desea establecer las propiedades de la relación propiamente dicha.

 Cuando se crea un elemento de esta manera, se crea automáticamente un conector en el diagrama, pero tiene una forma de manera predeterminada, el color y otras características. Para controlar cómo se crea el conector asociado, vea [creación de un elemento y su forma](#merge).

##  <a name="deleteelements"></a> Eliminar elementos
 Eliminar un elemento mediante una llamada a `Delete()`:

 `henry.Delete();`

 Esta operación, también se eliminarán:

-   Vínculos de relación hacia y desde el elemento. Por ejemplo, `edward.Parents` ya no contendrá `henry`.

-   Elementos de las funciones para que la `PropagatesDelete` indicador es true. Por ejemplo, se eliminarán la forma que muestre el elemento.

 De forma predeterminada, cada relación de incrustación tiene `PropagatesDelete` verdadera en el rol de destino. Eliminar `henry` no elimina el `familyTree`, pero `familyTree.Delete()` tendría que eliminar todo el `Persons`. Para obtener más información, consulte [personalizar el comportamiento de eliminación](../modeling/customizing-deletion-behavior.md).

 De forma predeterminada, `PropagatesDelete` no es cierto para los roles de relaciones de referencia.

 También puede hacer que las reglas de eliminación omitir propagaciones específicos cuando se elimina un objeto. Esto es útil si sustituye un elemento de otro. Suministre el GUID de uno o varios roles para los que no se propaguen eliminación. Puede obtener el GUID de la clase de relación:

 `henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`

 (Este ejemplo concreto no tendría ningún efecto, porque `PropagatesDelete` es `false` para los roles de la `ParentsHaveChildren` relación.)

 En algunos casos, se impide la eliminación por la existencia de un bloqueo, ya sea en el elemento o en un elemento que eliminaría la propagación. Puede usar `element.CanDelete()` para comprobar si se puede eliminar el elemento.

##  <a name="deletelinks"></a> Eliminar vínculos de relación
 Puede eliminar un vínculo de relación mediante la eliminación de un elemento de una propiedad de rol:

 `henry.Children.Remove(edward); // or:`

 `edward.Parents.Remove(henry);  // or:`

 También puede eliminar el vínculo de forma explícita:

 `edwardHenryLink.Delete();`

 Estos tres métodos todos tienen el mismo efecto. Sólo debe usar uno de ellos.

 Si el rol tiene una multiplicidad de 0.. 1 o 1.. 1, puede establecerlo en `null`, o con otro valor:

 `edward.FamilyTreeModel = null;` o:

 `edward.FamilyTreeModel = anotherFamilyTree;`

##  <a name="reorder"></a> Volver a ordenar los vínculos de una relación
 Los vínculos de una relación determinada que se origina o destinada a un elemento de modelo determinado tienen una secuencia concreta. Aparecen en el orden en que se agregaron. Por ejemplo, esta instrucción siempre dará a los elementos secundarios en el mismo orden:

 `foreach (Person child in henry.Children) ...`

 Puede cambiar el orden de los vínculos:

 `ParentsHaveChildren link = GetLink(henry,edward);`

 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`

 `DomainRoleInfo role =`

 `link.GetDomainRelationship().DomainRoles[0];`

 `link.MoveBefore(role, nextLink);`

##  <a name="locks"></a> Bloqueos
 Los cambios pueden evitarse con un bloqueo. Los bloqueos se pueden establecer en elementos individuales, en particiones y en el almacén. Si cualquiera de estos niveles tiene un bloqueo que evita que el tipo de cambio que desea realizar, podría producirá una excepción al intentarlo. Puede detectar si los bloqueos se establecen mediante el elemento. GetLocks(), que es un método de extensión que se define en el espacio de nombres <xref:Microsoft.VisualStudio.Modeling.Immutability>.

 Para obtener más información, consulte [definir una directiva de bloqueo para crear segmentos de sólo lectura](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).

##  <a name="copy"></a> Copiar y pegar
 Puede copiar elementos o grupos de elementos a un <xref:System.Windows.Forms.IDataObject>:

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

 `Merge ()` puede aceptar en un `PresentationElement` o `ModelElement`. Si le diera un `PresentationElement`, también puede especificar una posición en el diagrama de destino como tercer parámetro.

##  <a name="diagrams"></a> Navegar y actualizar diagramas
 En un ADSL, el elemento de modelo de dominio, que representa un concepto como persona o una canción, es independiente del elemento de forma que representa lo que ve en el diagrama. El elemento de modelo de dominio almacena las propiedades importantes y las relaciones de los conceptos. El elemento forma almacena el tamaño, la posición y el color de la vista del objeto en el diagrama y el diseño de los componentes.

### <a name="presentation-elements"></a>Elementos de presentación
 ![Diagrama de clases de forma base y tipos de elementos](../modeling/media/dslshapesandelements.png)

 En la definición DSL, cada elemento que especifique crea una clase que se deriva de una de las siguientes clases estándares.

|Tipo de elemento|Clase base|
|---------------------|----------------|
|Clase de dominio|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|
|Relación de dominio|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|
|Forma|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|
|Conector|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|
|Diagram|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|

 Normalmente, un elemento en un diagrama representa un elemento del modelo. Normalmente (aunque no siempre), un <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> representa una instancia de la clase de dominio y un <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> representa una instancia de la relación de dominio. El <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relación vincula una forma de nodo o un vínculo al elemento de modelo que representa.

 Cada forma de nodo o vínculo pertenece a un diagrama. Una forma de vínculo binario conecta a dos formas de nodo.

 Formas pueden tener formas secundarias en dos conjuntos. Una forma en la `NestedChildShapes` conjunto se limita a cuadro de límite de su elemento primario. Una forma en la `RelativeChildShapes` lista puede aparecer fuera o en parte fuera de los límites del elemento primario: por ejemplo, una etiqueta o un puerto. Un diagrama no tiene ningún `RelativeChildShapes` y no `Parent`.

###  <a name="views"></a> Navegar entre las formas y elementos
 Elementos del modelo de dominio y los elementos de forma que estén relacionados mediante la <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relación.

```csharp
// using Microsoft.VisualStudio.Modeling;
// using Microsoft.VisualStudio.Modeling.Diagrams;
// using System.Linq;
Person henry = ...;
PersonShape henryShape =
  PresentationViewsSubject.GetPresentation(henry)
    .FirstOrDefault() as PersonShape;
```

 La misma relación vincula las relaciones con conectores en el diagrama:

```
Descendants link = Descendants.GetLink(henry, edward);
DescendantConnector dc =
   PresentationViewsSubject.GetPresentation(link)
     .FirstOrDefault() as DescendantConnector;
// dc.FromShape == henryShape && dc.ToShape == edwardShape
```

 Esta relación también incluye vínculos a la raíz del modelo para el diagrama:

```
FamilyTreeDiagram diagram =
   PresentationViewsSubject.GetPresentation(familyTree)
      .FirstOrDefault() as FamilyTreeDiagram;
```

 Para obtener el elemento de modelo representado por una forma, use:

 `henryShape.ModelElement as Person`

 `diagram.ModelElement as FamilyTreeModel`

### <a name="navigating-around-the-diagram"></a>Navegar por el diagrama
 En general no es aconsejable para navegar entre las formas y conectores en el diagrama. Es mejor navegar por las relaciones en el modelo, moverse entre las formas y conectores solo cuando sea necesario para que funcione la apariencia del diagrama. Estos métodos vinculan conectores a las formas en cada extremo.

 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`

 `connector.FromShape, connector.ToShape`

 Muchas de las formas están compuestos; se compone de una forma principal y una o varias capas de elementos secundarios. Formas que se sitúan en relación con otra forma se dice que su *elementos secundarios*. Cuando se mueve la forma principal, los elementos secundarios se mueven con él.

 *Elementos secundarios relativos* puede aparecer fuera del cuadro de límite de la forma principal. *Anidar* elementos secundarios aparecen estrictamente dentro de los límites del elemento primario.

 Para obtener el conjunto superior de formas en un diagrama, use:

 `Diagram.NestedChildShapes`

 Las clases de antecesores de formas y conectores son:

 <xref:Microsoft.VisualStudio.Modeling.ModelElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>

 ------- *YourShape*

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 --------- *YourConnector*

###  <a name="shapeProperties"></a> Propiedades de formas y conectores
 En la mayoría de los casos, no es necesario realizar cambios explícitos en las formas. Cuando se han cambiado los elementos del modelo, las reglas de "corregir" actualizan las formas y conectores. Para obtener más información, consulte [responder a y propagar los cambios](../modeling/responding-to-and-propagating-changes.md).

 Sin embargo, es útil realizar algunos cambios explícitas en las formas en las propiedades que son independientes de los elementos del modelo. Por ejemplo, puede cambiar estas propiedades:

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A> -Determina el alto y ancho de la forma.

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A> -posición con respecto a la forma principal o diagrama

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A> -el conjunto de lápices y pinceles usados para dibujar la forma o conector

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A> -hace que la forma sea invisible

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A> -hace visible después de la forma un `Hide()`

###  <a name="merge"></a> Creación de un elemento y su forma
 Al crear un elemento y vincularla al árbol de incrustación relaciones, se crea automáticamente una forma y se asociados a él. Para ello, las reglas de "corrección" que se ejecutan al final de la transacción. Sin embargo, la forma aparecerá en una ubicación que se asignan automáticamente, y su forma, color y otras características tienen sus valores predeterminados. Para controlar cómo se crea la forma, puede usar la función de combinación. Debe agregar primero los elementos que desea agregar a un ElementGroup y, a continuación, combinar el grupo en el diagrama.

 Este método:

-   Establece el nombre, si ha asignado una propiedad como el nombre del elemento.

-   Se ajusta a las directivas de mezcla de elemento que ha especificado en la definición DSL.

 Este ejemplo crea una forma en la posición del mouse cuando el usuario hace doble clic en el diagrama. En la definición DSL para este ejemplo, el `FillColor` propiedad de `ExampleShape` ha sido expuesto.

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

 Si proporciona más de una forma, configurará sus posiciones relativas utilizando el `AbsoluteBounds`.

 También puede establecer el color y otras propiedades expuestas de conectores con este método.

### <a name="use-transactions"></a>Usar transacciones
 Formas, conectores y diagramas son subtipos de <xref:Microsoft.VisualStudio.Modeling.ModelElement> y activos en el almacén. Por lo tanto, debe realizar cambios en ellos solo dentro de una transacción. Para obtener más información, consulte [Cómo: usar transacciones para actualizar el modelo](../modeling/how-to-use-transactions-to-update-the-model.md).

##  <a name="docdata"></a> Vista de documento y los datos del documento
 ![Diagrama de clases de tipos de diagrama estándar](../modeling/media/dsldiagramsanddocs.png)

## <a name="store-partitions"></a>Almacenar particiones
 Cuando se carga un modelo, se carga en el diagrama que lo acompaña al mismo tiempo. Por lo general, el modelo se carga en Store.DefaultPartition, y se carga el contenido del diagrama en otra partición. Normalmente, se carga el contenido de cada partición y se guarda en un archivo independiente.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Modeling.ModelElement>
- [La validación en los lenguajes específicos de dominio](../modeling/validation-in-a-domain-specific-language.md)
- [Generar código a partir de lenguajes específicos de dominio](../modeling/generating-code-from-a-domain-specific-language.md)
- [Cómo: Usar transacciones para actualizar el modelo](../modeling/how-to-use-transactions-to-update-the-model.md)
- [Integrar modelos mediante Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Responder a los cambios y propagarlos](../modeling/responding-to-and-propagating-changes.md)
