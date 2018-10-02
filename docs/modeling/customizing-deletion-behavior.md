---
title: Personalizar el comportamiento de eliminación
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.deletebehavior
helpviewer_keywords:
- Domain-Specific Language, deletion
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: f7c05d76aa74e32695d20b2d5e9ed4f030e65813
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859814"
---
# <a name="customizing-deletion-behavior"></a>Personalizar el comportamiento de eliminación
Normalmente, al eliminar un elemento también se eliminan los elementos relacionados. Se eliminan todas las relaciones conectadas a él y todos los elementos secundarios. Este comportamiento se denomina *eliminar propagación*. Puede personalizar la propagación de la eliminación, por ejemplo, para organizar que se eliminen otros elementos relacionados. Escribiendo código de programa puede hacer que la propagación de la eliminación dependa del estado del modelo. También puede hacer que se produzcan otros cambios en respuesta a una eliminación.

 En este tema, se incluyen las siguientes secciones:

-   [Comportamiento de eliminación predeterminado](#default)

-   [Establecer la opción de propagar la eliminación de un rol](#property)

-   [Invalidar el cierre de la eliminación](#closure) -Use esta técnica donde eliminación podría provocar la eliminación de los elementos vecinos.

-   [Usar OnDeleting y OnDeleted](#ondeleting) -usar estos métodos en la respuesta puede incluir otras acciones como actualizar un valor dentro o fuera de la tienda.

-   [Reglas de eliminación](#rules) -usar reglas para propagar las actualizaciones de cualquier tipo dentro de la tienda, donde podría provocar un cambio a otros usuarios.

-   [Eventos de eliminación](#rules) -eventos de almacenamiento de uso para propagar las actualizaciones fuera de la tienda, por ejemplo a otros documentos de Visual Studio.

-   [UnMerge](#unmerge) -use la operación UnMerge para deshacer la operación de combinación que asoció un elemento secundario a su elemento primario.

## <a name="default"></a> Comportamiento de eliminación predeterminado
 De forma predeterminada, la propagación de la eliminación cumple estas reglas:

-   Si un elemento se elimina, todos los elementos incrustados también se eliminan. Los elementos incrustados son los destinos de relación de incrustación para las cuales este elemento es el origen. Por ejemplo, si hay una relación de incrustación de **álbum** a **canción**, a continuación, cuando se elimina un Album determinado, todas sus Songs se eliminarán también.

     En cambio, al eliminar una canción no se elimina el álbum.

-   De forma predeterminada, la eliminación no se propaga por las relaciones de referencia. Si no hay una relación de referencia **ArtistPlaysOnAlbum** desde **álbum** a **artista**, al eliminar un álbum no elimina el artista relacionado y al eliminar un artista no se elimina ningún álbum.

     Sin embargo, la eliminación sí se propaga por algunas relaciones integradas. Por ejemplo, cuando se elimina un elemento de modelo, su forma en el diagrama también se elimina. El elemento y la forma están relacionados mediante la relación de referencia `PresentationViewsSubject`.

-   Todas las relaciones que están conectadas al elemento, ya sea en el rol de origen o de destino, se eliminan. La propiedad de rol del elemento en el rol opuesto ya no contiene el elemento eliminado.

## <a name="property"></a> Establecer la opción de propagar la eliminación de un rol
 Puede hacer que la eliminación se propague a lo largo de una relación de referencia, o desde un elemento secundario incrustado a su primario.

#### <a name="to-set-delete-propagation"></a>Para establecer la propagación de la eliminación

1.  En el diagrama de definición de DSL, seleccione el *rol* al que quiera propagar la eliminación. El rol está representado por la línea situada a la izquierda o derecha de un cuadro de relación de dominio.

     Por ejemplo, si quiere especificar que siempre que se elimine un Album se eliminen también los Artists relacionados, seleccione el rol que está conectado a la clase de dominio Artist.

2.  En la ventana Propiedades, establezca la **propaga eliminar** propiedad.

3.  Presione F5 y compruebe que:

    -   Cuando se elimina una instancia de esta relación, también se elimina el elemento en el rol seleccionado.

    -   Cuando se elimina un elemento en el rol opuesto, se eliminarán las instancias de esta relación así como los elementos relacionados en este rol.

 También puede ver el **propaga eliminar** opción el **detalles de DSL** ventana. Seleccione una clase de dominio y, en la ventana Detalles de DSL, abra el **comportamiento al eliminar** página haciendo clic en el botón situado en el lado de la ventana. El **Propagate** opción estará disponible para el rol opuesto de cada relación. El **Eliminar estilo** columna indica si el **Propagate** opción está en su valor predeterminado, pero no tiene ningún efecto diferente.

## <a name="delete-propagation-by-using-program-code"></a>Propagación de la eliminación mediante código de programa
 Las opciones del archivo DSL Definition (Definición de DSL) solo le permiten elegir si la eliminación se propagará al vecino inmediato. Para implementar un esquema más complejo de propagación de la eliminación, puede escribir código de programa.

> [!NOTE]
>  Para agregar código de programa a la definición de DSL, cree un archivo de código independiente en el **Dsl** del proyecto y escriba definiciones parciales para aumentar las clases en la carpeta Generated Code. Para obtener más información, consulte [escribir código para personalizar lenguajes específicos de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md).

## <a name="closure"></a> Definir un cierre de eliminación
 La operación de eliminación usa la clase _Sumodelo_**DeleteClosure** para determinar qué elementos eliminará, dada una selección inicial. Llama a `ShouldVisitRelationship()` y a `ShouldVisitRolePlayer()` repetidamente, recorriendo el gráfico de relaciones. Puede invalidar estos métodos. Shouldvisitroleplayer incluye la identidad de un vínculo y el elemento en uno de los roles del vínculo. Debe devolver uno de los siguientes valores:

-   **VisitorFilterResult.Yes**: se debe eliminar el elemento y el rastreador debe continuar para probar otros vínculos del elemento.

-   **VisitorFilterResult.DoNotCare** -no se debe eliminar el elemento a menos que otra consulta responda que debe eliminarse.

-   **VisitorFilterResult.Never** -el elemento no se debe eliminar, aunque otra consulta responda **Sí**, y el rastreador no debe probar otros vínculos del elemento.

```
// When a musician is deleted, delete their albums with a low rating.
// Override methods in <YourDsl>DeleteClosure in DomainModel.cs
partial class MusicLibDeleteClosure
{
  public override VisitorFilterResult ShouldVisitRolePlayer
    (ElementWalker walker, ModelElement sourceElement, ElementLink elementLink,
    DomainRoleInfo targetDomainRole, ModelElement targetRolePlayer)
  {
    ArtistAppearsInAlbum link = elementLink as ArtistAppearsInAlbum;
    if (link != null
       && targetDomainRole.RolePlayer.Id == Album.DomainClassId)
    {
      // Count other unvisited links to the Album of this link.
      if (ArtistAppearsInAlbum.GetLinksToArtists(link.Album)
              .Where(linkAlbumArtist =>
                     linkAlbumArtist != link &&
                     !walker.Visited(linkAlbumArtist))
              .Count() == 0)
      {
        // Should delete this role player:
        return VisitorFilterResult.Yes;
      }
      else
        // Don't delete unless another relationship deletes it:
        return VisitorFilterResult.DoNotCare;
    }
    else
    {
      // Test for and respond to other relationships and roles here.

      // Not the relationship or role we're interested in.
      return base.ShouldVisitRolePlayer(walker, sourceElement,
             elementLink, targetDomainRole, targetRolePlayer);
    }
  }
}

```

 La técnica de cierre garantiza que el conjunto de elementos y vínculos que se va a eliminar se determine antes de comenzar la eliminación. El rastreador también combina los resultados del cierre con los de otras partes del modelo.

 Sin embargo, la técnica se da por supuesto que eliminación afecta solo a los vecinos en el gráfico de relaciones: no se puede usar este método para eliminar un elemento en otra parte del modelo. No puede usarlo si quiere agregar elementos o realizar otros cambios en respuesta a una eliminación.

## <a name="ondeleting"></a> Usar OnDeleting y OnDeleted
 Puede invalidar `OnDeleting()` o `OnDeleted()` en una clase de dominio o en una relación de dominio.

1.  Se llama a <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleting%2A> cuando se está a punto de eliminar un elemento, pero antes de que sus relaciones se hayan desconectado. Aún se puede navegar hacia y desde otros elementos, y aún está en `store.ElementDirectory`.

     Si se eliminan varios elementos al mismo tiempo, se llama a OnDeleting para todos ellos antes de realizar las eliminaciones.

     `IsDeleting` es True.

2.  Se llama a <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleted%2A> cuando el elemento se ha eliminado. Permanece en el montón de CLR para que se pueda realizar una acción de deshacer si es necesario, pero se desvincula de otros elementos y se quita de `store.ElementDirectory`. Para las relaciones, los roles aún hacen referencia los antiguos encargados de rol.`IsDeleted` es true.

3.  Se llama a OnDeleting y OnDeleted cuando el usuario invoca a Undo después de crear un elemento y cuando se repite una eliminación anterior en Redo. Use `this.Store.InUndoRedoOrRollback` para evitar actualizar los elementos del almacén en estos casos. Para obtener más información, consulte [Cómo: usar transacciones para actualizar el modelo](../modeling/how-to-use-transactions-to-update-the-model.md).

 Por ejemplo, el código siguiente elimina un Album cuando se elimina su último objeto Song secundario:

```

// Delete the parent Album when the last Song is deleted.
// Override methods in the embedding relationship between Album and Song:
partial class AlbumHasSongs
{
  protected override void OnDeleted()
  {
    base.OnDeleted();
    // Don't perform in-store actions in undo:
    if (this.Store.InUndoRedoOrRollback) return;
    // Relationship source and target still work:
    // Don't bother if source is already on its way out:
    if (!this.Album.IsDeleting && !this.Album.IsDeleted)
    {
      if (this.Album.Songs.Count == 0)
      {
        this.Album.Delete();
} } } }

```

 Suele ser más útil desencadenar desde la eliminación de la relación que desde el elemento de rol, porque funciona cuando se elimina el elemento y cuando se elimina la propia relación. Sin embargo, en las relaciones de referencia, quizás quiera propagar la eliminación cuando se elimine un elemento relacionado, pero no cuando se elimine la propia relación. En este ejemplo se elimina un Album cuando se elimina el último Artist contribuyente, pero no responde si las relaciones se eliminan:

```
using System.Linq; ...
// Assumes a many-many reference relationship
// between Artist and Album.
partial class Artist
{
  protected override void OnDeleting()
  {
    base.OnDeleting();
    if (this.Store.InUndoRedoOrRollback) return;
    List<Album> toDelete = new List<Album>();
    foreach (Album album in this.Albums)
    {
      if (album.Artists.Where(artist => !artist.IsDeleting)
                        .Count() == 0)
      {
        toDelete.Add(album);
      }
    }
    foreach (Album album in toDelete)
    {
      album.Delete();
} } }

```

 Cuando se realiza <xref:Microsoft.VisualStudio.Modeling.ModelElement.Delete%2A> en un elemento, se llamará a OnDeleting y OnDeleted. Estos métodos son siempre realizar insertada: es decir, inmediatamente antes y después de la eliminación real. Si el código elimina dos o más elementos, se llamará a OnDeleting y OnDeleted alternativamente en todos ellos, por turnos.

## <a name="rules"></a> Eventos y reglas de eliminación
 Como alternativa a los controladores de OnDelete, puede definir reglas de eliminación y eventos de eliminación.

1.  **Eliminando** y **eliminar** reglas se desencadenan solo en una transacción y no en Undo o Redo. Puede establecerlas para que se pongan en la cola de ejecución al final de la transacción en la que se realiza la eliminación. Las reglas Deleting se ejecutan siempre antes que las reglas Deleted que están en la cola.

     Use las reglas para propagar los cambios que afectan solo a los elementos del almacén, incluidas las relaciones, los elementos del diagrama y sus propiedades. Normalmente, las reglas Deleting se usan para propagar la eliminación, y las reglas Delete se usan para crear elementos y relaciones de sustitución.

     Para obtener más información, consulte [propagar cambios en el modelo de reglas de](../modeling/rules-propagate-changes-within-the-model.md).

2.  **Eliminar** eventos de almacén se invoca al final de una transacción y se llama después de undo o redo. Por lo tanto, puede usarse para propagar eliminaciones a objetos fuera de la tienda como archivos, las entradas de la base de datos u otros objetos en Visual Studio.

     Para obtener más información, consulte [controladores propagar los cambios fuera el modelo de evento](../modeling/event-handlers-propagate-changes-outside-the-model.md).

    > [!WARNING]
    >  Una vez eliminado un elemento, puede acceder a los valores de sus propiedades de dominio pero no puede navegar por los vínculos de relación. Sin embargo, si establece un evento de eliminación en una relación, también puede acceder a los dos elementos que eran sus encargados de rol. Por lo tanto, si desea responder a la eliminación de un elemento de modelo pero quiere acceder a un elemento al que estaba vinculado, establezca un evento de eliminación en la relación en lugar de la clase de dominio del elemento de modelo.

### <a name="example-deletion-rules"></a>Ejemplo de reglas de eliminación

```
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]
internal class AlbumDeletingRule : DeletingRule
{
  public override void ElementDeleting(ElementDeletingEventArgs e)
  {
    base.ElementDeleting(e);
    // ...perform tasks to propagate imminent deletion
  }
}
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]
internal class AlbumDeletedRule : DeleteRule
{
  public override void ElementDeleted(ElementDeletedEventArgs e)
  {
    base.ElementDeleted(e);
    // ...perform tasks such as creating new elements
  }
}

// The rule must be registered:
public partial class MusicLibDomainModel
{
  protected override Type[] GetCustomDomainModelTypes()
  {
    List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
    types.Add(typeof(AlbumDeletingRule));
    types.Add(typeof(AlbumDeletedRule));
    // If you add more rules, list them here.
    return types.ToArray();
  }
}

```

### <a name="example-deleted-event"></a>Ejemplo de evento Deleted

```
partial class NestedShapesSampleDocData
{
  protected override void OnDocumentLoaded(EventArgs e)
  {
    base.OnDocumentLoaded(e);
    DomainRelationshipInfo commentRelationship =
          this.Store.DomainDataDirectory
          .FindDomainRelationship(typeof(CommentsReferenceComponents));

    this.Store.EventManagerDirectory.ElementDeleted.Add(commentRelationship,
      new EventHandler<ElementDeletedEventArgs>(CommentLinkDeleted));
  }

  private void CommentLinkDeleted (object sender, ElementDeletedEventArgs e)
  {
    CommentsReferenceComponents link = e.ModelElement as CommentsReferenceComponents;
    Comment comment = link.Comment;
    Component component = link.Subject;
    if (comment.IsDeleted)
    {
      // The link was deleted because the comment was deleted.
      System.Windows.Forms.MessageBox.Show("Removed comment on " + component.Name);
    }
    else
    {
      // It was just the link that was deleted - the comment itself remains.
      System.Windows.Forms.MessageBox.Show("Removed comment link to "
           + component.Name);
    }
  }
}

```

## <a name="unmerge"></a> Separar
 La operación que asocia un elemento secundario a su elemento primario se denomina *mezcla*. Se produce cuando un nuevo elemento o grupo de elementos se crea con el cuadro de herramientas, se mueve desde otra parte del modelo o se copia desde el portapapeles. Además de crear una relación de incrustación entre el primario y su nuevo secundario, la operación de combinación también puede configurar otras relaciones, crear elementos auxiliares y establecer valores de propiedad en los elementos. La operación de combinación se encapsula en una directiva de combinación de elementos (EMD).

 Una EMD también encapsula la *unmerge* o `MergeDisconnect` operación. Si tiene un grupo de elementos que se ha construido mediante una combinación, se recomienda usar la operación anular combinación asociada para quitar un elemento del grupo, si quiere dejar los demás elementos en un estado coherente. La operación anular combinación normalmente usará las técnicas descritas en las secciones anteriores.

 Para obtener más información, consulte [personalizar la creación de elemento y el movimiento](../modeling/customizing-element-creation-and-movement.md).

## <a name="see-also"></a>Vea también

- [Personalizar comportamiento de copia](../modeling/customizing-copy-behavior.md)
- [Personalizar la creación y el movimiento de los elementos](../modeling/customizing-element-creation-and-movement.md)
- [Escribir código para personalizar lenguajes específicos de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)