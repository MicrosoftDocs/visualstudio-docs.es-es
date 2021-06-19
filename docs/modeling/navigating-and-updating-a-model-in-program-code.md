---
title: Navegar y actualizar un modelo en el código del programa
description: Aprenda a escribir código para crear y eliminar elementos del modelo, establecer sus propiedades y crear y eliminar vínculos entre elementos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: be19b34c51744c6bab1c6021a006f7ec9b4da0f4
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390976"
---
# <a name="navigate-and-update-a-model-in-program-code"></a>Navegar por un modelo en el código del programa y actualizarlo

Puede escribir código para crear y eliminar elementos del modelo, establecer sus propiedades y crear y eliminar vínculos entre elementos. Todos los cambios deben realizarse dentro de una transacción. Si los elementos se ven en un diagrama, el diagrama se "fijará" automáticamente al final de la transacción.

## <a name="an-example-dsl-definition"></a><a name="example"></a> Una definición de DSL de ejemplo
 Esta es la parte principal de DslDefinition.dsl para los ejemplos de este tema:

 ![Diagrama de definición de DSL &#45; modelo de árbol de familia](../modeling/media/familyt_person.png)

 Este modelo es una instancia de este DSL:

 ![Modelo de árbol de familia Tudor](../modeling/media/tudor_familytreemodel.png)

### <a name="references-and-namespaces"></a>Referencias y espacios de nombres
 Para ejecutar el código de este tema, debe hacer referencia a:

 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`

 El código usará este espacio de nombres:

 `using Microsoft.VisualStudio.Modeling;`

 Además, si está escribiendo el código en un proyecto diferente del en el que se define el DSL, debe importar el ensamblado creado por el proyecto dsl.

## <a name="navigating-the-model"></a><a name="navigation"></a> Navegar por el modelo

### <a name="properties"></a>Propiedades
 Las propiedades de dominio que se definen en la definición de DSL se convierten en propiedades a las que se puede acceder en el código del programa:

 `Person henry = ...;`

 `if (henry.BirthDate < 1500) ...`

 `if (henry.Name.EndsWith("VIII")) ...`

 Si desea establecer una propiedad, debe hacerlo dentro de una [transacción](#transaction):

 `henry.Name = "Henry VIII";`

 Si en la definición de DSL, la clase **de** una propiedad es **Calculated**, no se puede establecer. Para obtener más información, vea [Propiedades de almacenamiento calculadas y personalizadas.](../modeling/calculated-and-custom-storage-properties.md)

### <a name="relationships"></a>Relaciones
 Las relaciones de dominio que se definen en la definición de DSL se convierten en pares de propiedades, una en la clase en cada extremo de la relación. Los nombres de las propiedades aparecen en el diagrama DslDefinition como etiquetas en los roles de cada lado de la relación. Según la multiplicidad del rol, el tipo de la propiedad es la clase del otro extremo de la relación o una colección de esa clase.

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 Las propiedades en los extremos opuestos de una relación siempre son recíprocos. Cuando se crea o elimina un vínculo, se actualizan las propiedades de rol en ambos elementos. La siguiente expresión (que usa las extensiones de ) siempre es verdadera para `System.Linq` la relación ParentsChildren en el ejemplo:

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **ElementLinks**. Una relación también se representa mediante un elemento de modelo denominado *vínculo*, que es una instancia del tipo de relación de dominio. Un vínculo siempre tiene un elemento de origen y un elemento de destino. El elemento de origen y el elemento de destino pueden ser los mismos.

 Puede acceder a un vínculo y sus propiedades:

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 De forma predeterminada, no se permite que más de una instancia de una relación vincule ningún par de elementos del modelo. Pero si en la definición de DSL, la marca es true para la relación, puede haber más de un `Allow Duplicates` vínculo y debe usar `GetLinks` :

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 También hay otros métodos para acceder a los vínculos. Por ejemplo:

 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`

 **Roles ocultos.** Si en la definición de DSL, **Is Property Generated** es **false** para un rol determinado, no se genera ninguna propiedad que se corresponda con ese rol. Sin embargo, todavía puede acceder a los vínculos y recorrer los vínculos mediante los métodos de la relación:

 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`

 El ejemplo más usado es la relación , que vincula un elemento de modelo <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> a la forma que lo muestra en un diagrama:

 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`

### <a name="the-element-directory"></a>Directorio del elemento
 Puede acceder a todos los elementos del almacén mediante el directorio de elementos :

 `store.ElementDirectory.AllElements`

 También hay métodos para buscar elementos, como los siguientes:

 `store.ElementDirectory.FindElements(Person.DomainClassId);`

 `store.ElementDirectory.GetElement(elementId);`

## <a name="accessing-class-information"></a><a name="metadata"></a> Acceso a la información de clase
 Puede obtener información sobre las clases, las relaciones y otros aspectos de la definición de DSL. Por ejemplo:

 `DomainClassInfo personClass = henry.GetDomainClass();`

 `DomainPropertyInfo birthProperty =`

 `personClass.FindDomainProperty("BirthDate")`

 `DomainRelationshipInfo relationship =`

 `link.GetDomainRelationship();`

 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`

 Las clases antecesoras de los elementos del modelo son las siguientes:

- ModelElement: todos los elementos y relaciones son ModelElements

- ElementLink: todas las relaciones son ElementLinks

## <a name="perform-changes-inside-a-transaction"></a><a name="transaction"></a> Realizar cambios dentro de una transacción
 Cada vez que el código del programa cambia algo en store, debe hacerlo dentro de una transacción. Esto se aplica a todos los elementos del modelo, relaciones, formas, diagramas y sus propiedades. Para más información, consulte <xref:Microsoft.VisualStudio.Modeling.Transaction>.

 El método más conveniente para administrar una transacción es con una `using` instrucción incluida en una instrucción `try...catch` :

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

 Puede realizar cualquier número de cambios dentro de una transacción. Puede abrir nuevas transacciones dentro de una transacción activa.

 Para que los cambios se realicen de forma permanente, debe `Commit` realizar la transacción antes de que se deseche. Si se produce una excepción que no se detecta dentro de la transacción, store se restablecerá a su estado antes de los cambios.

## <a name="creating-model-elements"></a><a name="elements"></a> Crear elementos de modelo
 En este ejemplo se agrega un elemento a un modelo existente:

```csharp
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

 En este ejemplo se muestran estos puntos esenciales sobre la creación de un elemento:

- Cree el nuevo elemento en una partición específica de Store. Para los elementos y relaciones del modelo, pero no las formas, suele ser la partición predeterminada.

- Convertirla en el destino de una relación de inserción. En dsldefinition de este ejemplo, cada persona debe ser el destino de la relación de inserción FamilyTreeHasPeople. Para lograrlo, podemos establecer la propiedad de rol FamilyTreeModel del objeto Person o agregar la propiedad person a la propiedad de rol People del objeto FamilyTreeModel.

- Establezca las propiedades de un nuevo elemento, especialmente la propiedad para la que `IsName` es true en DslDefinition. Esta marca marca la propiedad que sirve para identificar el elemento de forma única dentro de su propietario. En este caso, la propiedad Name tiene esa marca.

- La definición de DSL de este DSL se debe haber cargado en store. Si está escribiendo una extensión como un comando de menú, esto suele ser ya true. En otros casos, puede cargar explícitamente el modelo en store o usar [ModelBus](/previous-versions/ee904639(v=vs.140)) para cargarlo. Para obtener más información, [vea Cómo: Abrir un modelo desde un archivo en código de programa.](../modeling/how-to-open-a-model-from-file-in-program-code.md)

  Cuando se crea un elemento de esta manera, se crea automáticamente una forma (si el DSL tiene un diagrama). Aparece en una ubicación asignada automáticamente, con forma predeterminada, color y otras características. Si desea controlar dónde y cómo aparece la forma asociada, vea [Crear un elemento y su forma](#merge).

## <a name="creating-relationship-links"></a><a name="links"></a> Crear vínculos de relación
 Hay dos relaciones definidas en la definición de DSL de ejemplo. Cada relación define una *propiedad de rol* en la clase en cada extremo de la relación.

 Hay tres maneras de crear una instancia de una relación. Cada uno de estos tres métodos tiene el mismo efecto:

- Establezca la propiedad del reproductor de roles de origen. Por ejemplo:

  - `familyTree.People.Add(edward);`

  - `edward.Parents.Add(henry);`

- Establezca la propiedad del reproductor de roles de destino. Por ejemplo:

  - `edward.familyTreeModel = familyTree;`

       La multiplicidad de este rol es `1..1` , por lo que asignamos el valor .

  - `henry.Children.Add(edward);`

       La multiplicidad de este rol es `0..*` , por lo que se agrega a la colección.

- Construya una instancia de la relación explícitamente. Por ejemplo:

  - `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`

  - `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`

  El último método es útil si desea establecer propiedades en la propia relación.

  Al crear un elemento de esta manera, se crea automáticamente un conector en el diagrama, pero tiene una forma, un color y otras características predeterminados. Para controlar cómo se crea el conector asociado, vea [Crear un elemento y su forma](#merge).

## <a name="deleting-elements"></a><a name="deleteelements"></a> Eliminación de elementos

Elimine un elemento mediante una llamada a `Delete()` :

`henry.Delete();`

Esta operación también eliminará:

- Vínculos de relación hacia y desde el elemento . Por ejemplo, `edward.Parents` ya no contendrá `henry` .

- Elementos en roles para los que la `PropagatesDelete` marca es true. Por ejemplo, se eliminará la forma que muestra el elemento.

De forma predeterminada, cada relación de inserción tiene `PropagatesDelete` true en el rol de destino. Al eliminar `henry` no se elimina , pero se `familyTree` `familyTree.Delete()` eliminarían todos los elementos `Persons` .

De forma predeterminada, `PropagatesDelete` no se aplica a los roles de las relaciones de referencia.

Puede hacer que las reglas de eliminación omitan propagacións específicas al eliminar un objeto. Esto resulta útil si va a sustituir un elemento por otro. Proporcione el GUID de uno o varios roles para los que no se debe propagar la eliminación. El GUID se puede obtener de la clase de relación:

`henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`

(Este ejemplo concreto no tendría ningún efecto, porque `PropagatesDelete` es para los roles de la `false` `ParentsHaveChildren` relación).

En algunos casos, la eliminación se impide mediante la existencia de un bloqueo, ya sea en el elemento o en un elemento que se eliminaría mediante la propagación. Puede usar `element.CanDelete()` para comprobar si el elemento se puede eliminar.

## <a name="deleting-relationship-links"></a><a name="deletelinks"></a> Eliminar vínculos de relación
 Puede eliminar un vínculo de relación quitando un elemento de una propiedad de rol:

 `henry.Children.Remove(edward); // or:`

 `edward.Parents.Remove(henry);  // or:`

 También puede eliminar el vínculo explícitamente:

 `edwardHenryLink.Delete();`

 Todos estos tres métodos tienen el mismo efecto. Solo tiene que usar uno de ellos.

 Si el rol tiene multiplicidad 0...1 o 1..1, puede establecerlo en , o `null` en otro valor:

 `edward.FamilyTreeModel = null;` O:

 `edward.FamilyTreeModel = anotherFamilyTree;`

## <a name="re-ordering-the-links-of-a-relationship"></a><a name="reorder"></a> Volver a ordenar los vínculos de una relación
 Los vínculos de una relación determinada que tienen como origen o destino un elemento de modelo determinado tienen una secuencia específica. Aparecen en el orden en que se agregaron. Por ejemplo, esta instrucción siempre dará como resultado los secundarios en el mismo orden:

 `foreach (Person child in henry.Children) ...`

 Puede cambiar el orden de los vínculos:

 `ParentsHaveChildren link = GetLink(henry,edward);`

 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`

 `DomainRoleInfo role =`

 `link.GetDomainRelationship().DomainRoles[0];`

 `link.MoveBefore(role, nextLink);`

## <a name="locks"></a><a name="locks"></a> Cerraduras
 Es posible que los cambios se impidan mediante un bloqueo. Los bloqueos se pueden establecer en elementos individuales, en particiones y en el almacén. Si alguno de estos niveles tiene un bloqueo que impide el tipo de cambio que desea realizar, es posible que se produce una excepción al intentarlo. Puede detectar si los bloqueos se establecen mediante el elemento . GetLocks(), que es un método de extensión que se define en el espacio de nombres <xref:Microsoft.VisualStudio.Modeling.Immutability> .

 Para obtener más información, vea [Definir una directiva de bloqueo para crear Read-Only segmentos](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).

## <a name="copy-and-paste"></a><a name="copy"></a> Copiar y pegar
 Puede copiar elementos o grupos de elementos en <xref:System.Windows.Forms.IDataObject> :

```csharp
Person person = personShape.ModelElement as Person;
Person adopter = adopterShape.ModelElement as Person;
IDataObject data = new DataObject();
personShape.Diagram.ElementOperations
      .Copy(data, person.Children.ToList<ModelElement>());
```

 Los elementos se almacenan como un grupo de elementos serializado.

 Puede combinar elementos de un objeto IDataObject en un modelo:

```csharp
using (Transaction t = targetDiagram.Store.
        TransactionManager.BeginTransaction("paste"))
{
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);
}
```

 `Merge ()` puede aceptar o `PresentationElement` `ModelElement` . Si le proporciona un `PresentationElement` , también puede especificar una posición en el diagrama de destino como un tercer parámetro.

## <a name="navigating-and-updating-diagrams"></a><a name="diagrams"></a> Navegación y actualización de diagramas
 En un DSL, el elemento de modelo de dominio, que representa un concepto como Person o Song, es independiente del elemento de forma, que representa lo que se ve en el diagrama. El elemento de modelo de dominio almacena las propiedades y relaciones importantes de los conceptos. El elemento de forma almacena el tamaño, la posición y el color de la vista del objeto en el diagrama y el diseño de sus partes del componente.

### <a name="presentation-elements"></a>Elementos de presentación
 ![Diagrama de clases de forma base y tipos de elementos](../modeling/media/dslshapesandelements.png)

 En la definición de DSL, cada elemento que especifique crea una clase que se deriva de una de las siguientes clases estándar.

|Tipo de elemento|Clase base|
|-|-|
|Clase de dominio|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|
|Relación de dominio|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|
|Forma|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|
|Conector|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|
|Diagrama|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|

 Un elemento de un diagrama normalmente representa un elemento de modelo. Normalmente (pero no siempre), representa una instancia de clase de <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> dominio y representa una instancia de relación de <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> dominio. La <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relación vincula una forma de nodo o vínculo al elemento de modelo que representa.

 Cada forma de nodo o vínculo pertenece a un diagrama. Una forma de vínculo binario conecta dos formas de nodo.

 Las formas pueden tener formas secundarias en dos conjuntos. Una forma del `NestedChildShapes` conjunto se limita al cuadro de límite de su elemento primario. Una forma de la lista puede aparecer fuera o parcialmente fuera de los límites del elemento primario, por ejemplo, una `RelativeChildShapes` etiqueta o un puerto. Un diagrama no tiene ni `RelativeChildShapes` . `Parent`

### <a name="navigating-between-shapes-and-elements"></a><a name="views"></a> Navegar entre formas y elementos
 Los elementos del modelo de dominio y los elementos de forma están relacionados por la <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relación.

```csharp
// using Microsoft.VisualStudio.Modeling;
// using Microsoft.VisualStudio.Modeling.Diagrams;
// using System.Linq;
Person henry = ...;
PersonShape henryShape =
  PresentationViewsSubject.GetPresentation(henry)
    .FirstOrDefault() as PersonShape;
```

 La misma relación vincula relaciones a conectores en el diagrama:

```
Descendants link = Descendants.GetLink(henry, edward);
DescendantConnector dc =
   PresentationViewsSubject.GetPresentation(link)
     .FirstOrDefault() as DescendantConnector;
// dc.FromShape == henryShape && dc.ToShape == edwardShape
```

 Esta relación también vincula la raíz del modelo al diagrama:

```
FamilyTreeDiagram diagram =
   PresentationViewsSubject.GetPresentation(familyTree)
      .FirstOrDefault() as FamilyTreeDiagram;
```

 Para obtener el elemento de modelo representado por una forma, use:

 `henryShape.ModelElement as Person`

 `diagram.ModelElement as FamilyTreeModel`

### <a name="navigating-around-the-diagram"></a>Navegar por el diagrama
 En general, no es aconsejable navegar entre formas y conectores en el diagrama. Es mejor navegar por las relaciones del modelo, moverse entre las formas y los conectores solo cuando sea necesario trabajar en la apariencia del diagrama. Estos métodos vinculan conectores a las formas de cada extremo:

 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`

 `connector.FromShape, connector.ToShape`

 Muchas formas son compuestos; están hechos de una forma primaria y una o varias capas de elementos secundarios. Se dice que las formas que se sitúan en relación con otra forma son sus *secundarios.* Cuando se mueve la forma primaria, los elementos secundarios se mueven con ella.

 *Los elementos secundarios* relativos pueden aparecer fuera del cuadro de límite de la forma primaria. *Los* elementos secundarios anidados aparecen estrictamente dentro de los límites del elemento primario.

 Para obtener el conjunto superior de formas de un diagrama, use:

 `Diagram.NestedChildShapes`

 Las clases antecesoras de formas y conectores son:

 <xref:Microsoft.VisualStudio.Modeling.ModelElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>

 ------- *YourShape*

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 --------- *YourConnector*

### <a name="properties-of-shapes-and-connectors"></a><a name="shapeProperties"></a> Propiedades de formas y conectores
 En la mayoría de los casos, no es necesario realizar cambios explícitos en las formas. Cuando haya cambiado los elementos del modelo, las reglas de "corrección" actualizan las formas y los conectores. Para obtener más información, [vea Responder a y propagar cambios.](../modeling/responding-to-and-propagating-changes.md)

 Sin embargo, resulta útil realizar algunos cambios explícitos en las formas de las propiedades que son independientes de los elementos del modelo. Por ejemplo, podría cambiar estas propiedades:

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A> : determina el alto y el ancho de la forma.

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A> : posición relativa a la forma o diagrama primarios

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A> : el conjunto de lápices y pinceles usados para dibujar la forma o el conector

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A> : hace que la forma sea invisible

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A> : hace que la forma sea visible después de un `Hide()`

### <a name="creating-an-element-and-its-shape"></a><a name="merge"></a> Crear un elemento y su forma

Al crear un elemento y vincularlo al árbol de relaciones de inserción, se crea automáticamente una forma y se asocia a él. Esto se hace mediante las reglas de "corrección" que se ejecutan al final de la transacción. Sin embargo, la forma aparecerá en una ubicación asignada automáticamente y su forma, color y otras características tendrán valores predeterminados. Para controlar cómo se crea la forma, puede usar la función merge. Primero debe agregar los elementos que desea agregar a un elemento ElementGroup y, a continuación, combinar el grupo en el diagrama.

Este método:

- Establece el nombre, si ha asignado una propiedad como nombre del elemento.

- Observa las directivas de combinación de elementos que especificó en la definición de DSL.

En este ejemplo se crea una forma en la posición del mouse, cuando el usuario hace doble clic en el diagrama. En la definición de DSL de este ejemplo, `FillColor` se ha expuesto la propiedad de `ExampleShape` .

```csharp
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

 Si proporciona más de una forma, establezca sus posiciones relativas mediante `AbsoluteBounds` .

 También puede establecer el color y otras propiedades expuestas de los conectores mediante este método.

### <a name="use-transactions"></a>Usar transacciones
 Las formas, los conectores y los diagramas son subtipos de <xref:Microsoft.VisualStudio.Modeling.ModelElement> y se encuentran en la Tienda. Por lo tanto, solo debe realizar cambios en ellos dentro de una transacción. Para obtener más información, [vea Cómo: Usar transacciones para actualizar el modelo.](../modeling/how-to-use-transactions-to-update-the-model.md)

## <a name="document-view-and-document-data"></a><a name="docdata"></a> Vista de documentos y datos de documentos
 ![Diagrama de clases de tipos de diagrama estándar](../modeling/media/dsldiagramsanddocs.png)

## <a name="store-partitions"></a>Almacenar particiones
 Cuando se carga un modelo, el diagrama que lo acompaña se carga al mismo tiempo. Normalmente, el modelo se carga en Store.DefaultPartition y el contenido del diagrama se carga en otra partición. Normalmente, el contenido de cada partición se carga y guarda en un archivo independiente.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Modeling.ModelElement>
- [La validación en los lenguajes específicos de dominio](../modeling/validation-in-a-domain-specific-language.md)
- [Generar código a partir de lenguajes específicos de dominio](../modeling/generating-code-from-a-domain-specific-language.md)
- [Cómo: Usar transacciones para actualizar el modelo](../modeling/how-to-use-transactions-to-update-the-model.md)
- [Integrar modelos mediante Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Responder a los cambios y propagarlos](../modeling/responding-to-and-propagating-changes.md)
