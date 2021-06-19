---
title: Los controladores de eventos propagan cambios fuera del modelo
description: Obtenga información sobre que, en el SDK de visualización y modelado, puede definir controladores de eventos de almacén para propagar los cambios a los recursos fuera del almacén.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 115d26840f321792712392367794e443e41543a2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388950"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Los controladores de eventos propagan cambios fuera del modelo

En el SDK de visualización y modelado, puede definir controladores de eventos de almacén para propagar los cambios a los recursos fuera del almacén, como variables que no son de almacén, archivos, modelos en otros almacenes u otras extensiones de Visual Studio. Los controladores de eventos de almacén se ejecutan después del final de la transacción en la que se produjo el evento de desencadenamiento. También se ejecutan en una operación deshacer o rehacer. Por lo tanto, a diferencia de las reglas de almacén, los eventos de almacén son más útiles para actualizar los valores que están fuera del almacén. A diferencia de los eventos de .NET, los controladores de eventos de almacén se registran para escuchar a una clase: no es necesario registrar un controlador independiente para cada instancia. Para obtener más información sobre cómo elegir entre diferentes formas de controlar los cambios, vea Responder a [y propagar cambios.](../modeling/responding-to-and-propagating-changes.md)

La superficie gráfica y otros controles de interfaz de usuario son ejemplos de recursos externos que se pueden controlar mediante eventos de almacenamiento.

### <a name="to-define-a-store-event"></a>Para definir un evento de almacén

1. Elija el tipo de evento que desea supervisar. Para obtener una lista completa, vea las propiedades de <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory> . Cada propiedad corresponde a un tipo de evento. Los tipos de eventos usados con más frecuencia son:

    - `ElementAdded` : se desencadena cuando se crea un elemento de modelo, un vínculo de relación, una forma o un conector.

    - ElementPropertyChanged: se desencadena cuando se cambia el valor de `Normal` una propiedad de dominio. El evento se desencadena solo si los valores nuevos y antiguos no son iguales. El evento no se puede aplicar a las propiedades de almacenamiento calculadas y personalizadas.

         No se puede aplicar a las propiedades de rol que corresponden a vínculos de relación. En su lugar, `ElementAdded` use para supervisar la relación de dominio.

    - `ElementDeleted` : se desencadena después de eliminar un elemento del modelo, una relación, una forma o un conector. Todavía puede acceder a los valores de propiedad del elemento, pero no tendrá ninguna relación con otros elementos.

2. Agregue una definición de clase parcial _para YourDsl_**DocData** en un archivo de código independiente en el **proyecto DslPackage.**

3. Escriba el código del evento como método, como en el ejemplo siguiente. Puede ser `static` , a menos que desee acceder a `DocData` .

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

## <a name="use-events-to-make-undoable-adjustments-in-the-store"></a>Usar eventos para realizar ajustes que se pueden deshacer en el almacén

Los eventos de almacén no se usan normalmente para propagar los cambios dentro del almacén, porque el controlador de eventos se ejecuta después de que se confirma la transacción. En su lugar, usaría una regla de almacén. Para obtener más información, vea [Reglas propagar cambios dentro del modelo](../modeling/rules-propagate-changes-within-the-model.md).

Sin embargo, podría usar un controlador de eventos para realizar actualizaciones adicionales en el almacén, si desea que el usuario pueda deshacer las actualizaciones adicionales por separado del evento original. Por ejemplo, supongamos que los caracteres en minúsculas son la convención habitual para los títulos del álbum. Puede escribir un controlador de eventos de almacén que corrija el título en minúsculas después de que el usuario lo haya escrito en mayúsculas. Pero el usuario podría usar el comando Deshacer para cancelar la corrección y restaurar los caracteres en mayúsculas. Una segunda fase deshacer quitaría el cambio del usuario.

Por el contrario, si escribió una regla de almacén para hacer lo mismo, el cambio del usuario y la corrección estarían en la misma transacción, de modo que el usuario no pudiera deshacer el ajuste sin perder el cambio original.

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

- Use `store.InUndoRedoOrRollback` para evitar realizar cambios en los elementos del modelo en Deshacer. El administrador de transacciones volverá a establecer todo el contenido del almacén en su estado original.

- Use `store.InSerializationTransaction` para evitar realizar cambios mientras el modelo se carga desde el archivo.

- Los cambios harán que se desencadene más eventos. Asegúrese de evitar un bucle infinito.

## <a name="store-event-types"></a>Almacenar tipos de eventos

Cada tipo de evento corresponde a una colección en Store.EventManagerDirectory. Puede agregar o quitar controladores de eventos en cualquier momento, pero es habitual agregarlos cuando se carga el documento.

|`EventManagerDirectory` Nombre de propiedad|Se ejecuta cuando|
|-|-|
|Elemento agregado|Se crea una instancia de una clase de dominio, una relación de dominio, una forma, un conector o un diagrama.|
|ElementDeleted|Se ha quitado un elemento de modelo del directorio de elementos del almacén y ya no es el origen ni el destino de ninguna relación. El elemento no se elimina realmente de la memoria, pero se conserva en caso de una futura deshacer.|
|ElementEventsBegun|Se invoca al final de una transacción externa.|
|ElementEventsEnded|Se invoca cuando se han procesado todos los demás eventos.|
|ElementMoved|Un elemento de modelo se ha movido de una partición de almacén a otra.<br /><br /> Esto no está relacionado con la ubicación de una forma en el diagrama.|
|ElementPropertyChanged|El valor de una propiedad de dominio ha cambiado. Esto solo se ejecuta si los valores antiguos y nuevos no son iguales.|
|RolePlayerChanged|Uno de los dos roles (extremos) de una relación hace referencia a un nuevo elemento.|
|RolePlayerOrderChanged|En un rol con multiplicidad mayor que 1, la secuencia de vínculos ha cambiado.|
|TransactionBeginning||
|TransactionCommitted||
|TransactionRolledBack||

## <a name="see-also"></a>Vea también

- [Responder a los cambios y propagarlos](../modeling/responding-to-and-propagating-changes.md)
- [Código de ejemplo: Diagramas de circuito](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
