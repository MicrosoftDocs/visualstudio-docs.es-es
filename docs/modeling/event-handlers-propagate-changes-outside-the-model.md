---
title: Los controladores de eventos propagan cambios fuera del modelo
description: Aprenda que en el SDK de visualización y modelado, puede definir controladores de eventos de almacén para propagar los cambios a los recursos fuera del almacén.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0ed45d631697d37db8da49e459e80f1b5a43a373
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935136"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Los controladores de eventos propagan cambios fuera del modelo

En el SDK de visualización y modelado, puede definir controladores de eventos de almacén para propagar los cambios a los recursos fuera del almacén, como las variables que no son de almacén, los archivos, los modelos de otros almacenes u otras extensiones de Visual Studio. Los controladores de eventos de almacenamiento se ejecutan después del final de la transacción en la que se produjo el evento de desencadenamiento. También se ejecutan en una operación de deshacer o rehacer. Por lo tanto, a diferencia de las reglas de almacenamiento, los eventos de almacén son más útiles para actualizar los valores que están fuera del almacén. A diferencia de los eventos de .NET, los controladores de eventos de almacén se registran para escuchar una clase: no es necesario registrar un controlador independiente para cada instancia. Para obtener más información sobre cómo elegir entre diferentes maneras de controlar los cambios, consulte [responder a los cambios y propagarlos](../modeling/responding-to-and-propagating-changes.md).

La superficie gráfica y otros controles de interfaz de usuario son ejemplos de recursos externos que los eventos de almacenamiento pueden controlar.

### <a name="to-define-a-store-event"></a>Para definir un evento de almacén

1. Elija el tipo de evento que desea supervisar. Para obtener una lista completa, examine las propiedades de <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory> . Cada propiedad corresponde a un tipo de evento. Los tipos de evento que se usan con más frecuencia son:

    - `ElementAdded` -se desencadena cuando se crea un elemento de modelo, un vínculo de relación, una forma o un conector.

    - ElementPropertyChanged: se desencadena cuando se cambia el valor de una `Normal` propiedad de dominio. El evento se desencadena solo si los valores nuevos y antiguos no son iguales. El evento no se puede aplicar a las propiedades de almacenamiento calculadas y personalizadas.

         No se puede aplicar a las propiedades de rol que corresponden a los vínculos de relación. En su lugar, use `ElementAdded` para supervisar la relación de dominio.

    - `ElementDeleted` -se desencadena cuando se ha eliminado un elemento de modelo, una relación, una forma o un conector. Todavía puede tener acceso a los valores de propiedad del elemento, pero no tendrá ninguna relación con otros elementos.

2. Agregue una definición de clase parcial para _sudsl_**en un archivo de código** independiente del proyecto **DslPackage** .

3. Escriba el código del evento como un método, como en el ejemplo siguiente. Puede ser `static` , a menos que desee tener acceso a `DocData` .

4. Invalide `OnDocumentLoaded()` para registrar el controlador. Si tiene más de un controlador, puede registrarlos todos en el mismo lugar.

La ubicación del código de registro no es crítica. `DocView.LoadView()` es una ubicación alternativa.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.VisualStudio.Modeling;

namespace Company.MusicLib
{
  partial class MusicLibDocData
  {
    // Register store events here or in DocView.LoadView().
    protected override void OnDocumentLoaded()
    {
      base.OnDocumentLoaded(); // Don't forget this.

      #region Store event handler registration.
      Store store = this.Store;
      EventManagerDirectory emd = store.EventManagerDirectory;
      DomainRelationshipInfo linkInfo = store.DomainDataDirectory
          .FindDomainRelationship(typeof(ArtistAppearsInAlbum));
      emd.ElementAdded.Add(linkInfo,
          new EventHandler<ElementAddedEventArgs>(AddLink));
      emd.ElementDeleted.Add(linkInfo,
          new EventHandler<ElementDeletedEventArgs>(RemoveLink));

      #endregion Store event handlers.
    }

    private void AddLink(object sender, ElementAddedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Add(link.Artist.Name, link.Album.Title);
    }
    private void RemoveLink(object sender, ElementDeletedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Delete(link.Artist.Name, link.Album.Title);
    }
  }
}
```

## <a name="use-events-to-make-undoable-adjustments-in-the-store"></a>Usar eventos para realizar ajustes que se puedan deshacer en el almacén

Normalmente, los eventos de almacén no se usan para propagar los cambios dentro del almacén, ya que el controlador de eventos se ejecuta después de confirmar la transacción. En su lugar, usaría una regla de almacén. Para obtener más información, vea [propagar los cambios dentro del modelo](../modeling/rules-propagate-changes-within-the-model.md).

Sin embargo, puede usar un controlador de eventos para realizar actualizaciones adicionales en el almacén, si desea que el usuario pueda deshacer las actualizaciones adicionales por separado del evento original. Por ejemplo, supongamos que los caracteres en minúsculas son la Convención habitual de los títulos de álbumes. Podría escribir un controlador de eventos de almacén que corrija el título a minúsculas después de que el usuario lo hubiera escrito en mayúsculas. Pero el usuario podría usar el comando Deshacer para cancelar la corrección y restaurar los caracteres en mayúsculas. Una segunda operación de deshacer quitaría el cambio del usuario.

Por el contrario, si ha escrito una regla de almacén para hacer lo mismo, el cambio del usuario y la corrección estarán en la misma transacción, por lo que el usuario no pudo deshacer el ajuste sin perder el cambio original.

```csharp
partial class MusicLibDocView
{
    // Register store events here or in DocData.OnDocumentLoaded().
    protected override void LoadView()
    {
      /* Register store event handler for Album Title property. */
      // Get reflection data for property:
      DomainPropertyInfo propertyInfo =
        this.DocData.Store.DomainDataDirectory
        .FindDomainProperty(Album.TitleDomainPropertyId);
      // Add to property handler list:
      this.DocData.Store.EventManagerDirectory
        .ElementPropertyChanged.Add(propertyInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));

      /*
      // Alternatively, you can set one handler for
      // all properties of a class.
      // Your handler has to determine which property changed.
      DomainClassInfo classInfo = this.Store.DomainDataDirectory
           .FindDomainClass(typeof(Album));
      this.Store.EventManagerDirectory
          .ElementPropertyChanged.Add(classInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));
       */
      return base.LoadView();
    }

// Undoable adjustment after a property is changed.
// Method can be static since no local access.
private static void AlbumTitleAdjuster(object sender,
         ElementPropertyChangedEventArgs e)
{
  Album album = e.ModelElement as Album;
  Store store = album.Store;

  // We mustn't update the store in an Undo:
  if (store.InUndoRedoOrRollback
      || store.InSerializationTransaction)
      return;

  if (e.DomainProperty.Id == Album.TitleDomainPropertyId)
  {
    string newValue = (string)e.NewValue;
    string lowerCase = newValue.ToLowerInvariant();
    if (!newValue.Equals(lowerCase))
    {
      using (Transaction t = store.TransactionManager
            .BeginTransaction("adjust album title"))
      {
        album.Title = lowerCase;
        t.Commit();
      } // Beware! This could trigger the event again.
    }
  }
  // else other properties of this class.
}
```

Si escribe un evento que actualiza el almacén:

- Use `store.InUndoRedoOrRollback` para evitar realizar cambios en los elementos del modelo en la operación de deshacer. El administrador de transacciones volverá a establecer todo en el almacén en su estado original.

- Use `store.InSerializationTransaction` para evitar realizar cambios mientras el modelo se carga desde el archivo.

- Los cambios provocarán que se desencadenen otros eventos. Asegúrese de evitar un bucle infinito.

## <a name="store-event-types"></a>Almacenar tipos de eventos

Cada tipo de evento corresponde a una colección en Store. EventManagerDirectory. Puede Agregar o quitar controladores de eventos en cualquier momento, pero es habitual agregarlos cuando se carga el documento.

|`EventManagerDirectory` Nombre de propiedad|Se ejecuta cuando|
|-|-|
|ElementAdded|Se crea una instancia de una clase de dominio, relación de dominio, forma, conector o diagrama.|
|ElementDeleted|Un elemento de modelo se ha quitado del directorio de elementos del almacén y ya no es el origen ni el destino de ninguna relación. En realidad, el elemento no se elimina de la memoria, sino que se conserva en el caso de una operación de deshacer futura.|
|ElementEventsBegun|Se invoca al final de una transacción externa.|
|Evento elementeventsended|Se invoca cuando se han procesado todos los demás eventos.|
|ElementMoved|Un elemento de modelo se ha pasado de una partición de almacén a otra.<br /><br /> Esto no está relacionado con la ubicación de una forma en el diagrama.|
|ElementPropertyChanged|El valor de una propiedad de dominio ha cambiado. Solo se ejecuta si los valores antiguos y nuevos no son iguales.|
|RolePlayerChanged|Uno de los dos roles (extremos) de una relación hace referencia a un nuevo elemento.|
|RolePlayerOrderChanged|En un rol con una multiplicidad mayor que 1, la secuencia de vínculos ha cambiado.|
|TransactionBeginning||
|TransactionCommitted||
|TransactionRolledBack||

## <a name="see-also"></a>Vea también

- [Responder a los cambios y propagarlos](../modeling/responding-to-and-propagating-changes.md)
- [Código de ejemplo: diagramas de circuitos](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
