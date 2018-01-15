---
title: Controladores de eventos propagan los cambios fuera del modelo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 717f61f440414370f3e9a2180e1c1cade7436aeb
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Los controladores de eventos propagan cambios fuera del modelo
En el SDK de modelado y visualización, puede definir controladores de eventos de almacén para propagar los cambios a los recursos fuera de la tienda, como variables no almacén, archivos, los modelos en otros almacenes, o en otro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensiones. Controladores de eventos de almacén se ejecutan después del final de la transacción en la que ocurrió el evento desencadenador. También se ejecutan en una operación de deshacer o rehacer. Por lo tanto, a diferencia del almacén de reglas, eventos de almacén son muy útiles para actualizar los valores que están fuera de la tienda. A diferencia de los eventos. NET, se registran los controladores de eventos de almacén para que escuche en una clase: no es necesario que registrar un controlador independiente para cada instancia. Para obtener más información sobre cómo elegir entre diferentes maneras de controlar los cambios, consulte [responder a y propagar los cambios](../modeling/responding-to-and-propagating-changes.md).  
  
 La superficie del gráfica y otros controles de interfaz de usuario son ejemplos de recursos externos que pueden ser controlados por eventos de almacén.  
  
### <a name="to-define-a-store-event"></a>Para definir un evento de almacén  
  
1.  Elija el tipo de evento que desea supervisar. Para obtener una lista completa, examine las propiedades de <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>. Cada propiedad se corresponde con un tipo de evento. Los usados con frecuencia son tipos de evento:  
  
    -   `ElementAdded`-se desencadena cuando un elemento del modelo, se crea el vínculo de relación, forma o conector.  
  
    -   ElementPropertyChanged - se desencadena cuando el valor de un `Normal` se cambia la propiedad de dominio. El evento se desencadena únicamente si los valores nuevos y antiguos no son iguales. El evento no se puede aplicar a las propiedades de almacenamiento personalizados y calculados.  
  
         No se puede aplicar a las propiedades de rol que corresponden a los vínculos de relación. En su lugar, use `ElementAdded` para supervisar la relación de dominio.  
  
    -   `ElementDeleted`-se desencadena después de un elemento del modelo, relación, forma o conector se ha eliminado. Todavía puede tener acceso a los valores de propiedad del elemento, pero no tendrá ninguna relación con otros elementos.  
  
2.  Agregar una definición de clase parcial para *YourDsl *** DocData** en un archivo de código independiente en el **DslPackage** proyecto.  
  
3.  Escriba el código del evento como un método, como en el ejemplo siguiente. Puede ser `static`, a menos que desee tener acceso a `DocData`.  
  
4.  Invalidar `OnDocumentLoaded()` para registrar el controlador. Si tiene más de un controlador, se puede registrar en el mismo lugar.  
  
 La ubicación del código de registro no es crítica. `DocView.LoadView()`es una ubicación alternativa.  
  
```  
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
  
## <a name="using-events-to-make-undoable-adjustments-in-the-store"></a>Uso de eventos para realizar ajustes que se pueden deshacer en el almacén  
 Eventos de almacén no se usan normalmente para propagar los cambios en el almacén, dado que el controlador de eventos se ejecuta una vez confirmada la transacción. En su lugar, debería usar una regla de almacén. Para obtener más información, consulte [propagar los cambios en el modelo de reglas de](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Sin embargo, puede utilizar un controlador de eventos para realizar actualizaciones adicionales en el almacén, si desea que el usuario para poder deshacer las actualizaciones adicionales por separado desde el evento original. Por ejemplo, suponga que los caracteres en minúsculas son la convención usual de títulos de álbum. Puede escribir un controlador de eventos de almacén que corrige el título a minúsculas después de que el usuario ha escrito en mayúsculas. Pero el usuario podría utilizar el comando Deshacer para cancelar la corrección, restaurar los caracteres en mayúsculas. Una segunda acción de deshacer quitará el cambio del usuario.  
  
 Por el contrario, si ha escrito una regla de almacén para hacer lo mismo, el cambio del usuario y la corrección estarían en la misma transacción, para que el usuario no pudo deshacer el ajuste sin perder los cambios originales.  
  
```  
  
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
  
-   Use `store.InUndoRedoOrRollback` para evitar realizar cambios en los elementos del modelo en Deshacer. El Administrador de transacciones se establecerá todos los elementos en el almacén a su estado original.  
  
-   Use `store.InSerializationTransaction` para evitar la realización de cambios mientras se carga el modelo de archivo.  
  
-   Los cambios hará más eventos que se desencadene. Asegúrese de evitar un bucle infinito.  
  
## <a name="store-event-types"></a>Tipos de eventos de almacén  
 Cada tipo de evento corresponde a una colección en Store.EventManagerDirectory. Puede agregar o quitar controladores de eventos en cualquier momento, pero es habitual para agregarlos al cargar el documento.  
  
|`EventManagerDirectory`Nombre de propiedad|Se ejecuta cuando|  
|-------------------------------------------|-------------------|  
|ElementAdded|Se crea una instancia de una clase de dominio, relación de dominio, forma, conector o diagrama.|  
|ElementDeleted|Un elemento del modelo se ha quitado de un directorio de elemento del almacén y ya no es el origen o destino de una relación. El elemento no se elimina realmente de la memoria, pero se conserva en el caso de una acción de deshacer futuras.|  
|ElementEventsBegun|Se invoca al final de una transacción externa.|  
|ElementEventsEnded|Se invoca cuando se hayan procesado todos los otros eventos.|  
|ElementMoved|Se ha movido un elemento del modelo de partición de un almacén a otro.<br /><br /> Esto no está relacionado con la ubicación de una forma del diagrama.|  
|ElementPropertyChanged|El valor de una propiedad de dominio ha cambiado. Esto se ejecuta sólo si los valores antiguos y nuevos no son iguales.|  
|RolePlayerChanged|Uno de los dos roles (extremos) de una relación hace referencia a un nuevo elemento.|  
|RolePlayerOrderChanged|En una función con una multiplicidad mayor que 1, ha cambiado la secuencia de vínculos.|  
|TransactionBeginning||  
|TransactionCommitted||  
|TransactionRolledBack||  
  
## <a name="see-also"></a>Vea también  
 [Responder a y propagación de cambios](../modeling/responding-to-and-propagating-changes.md)   
 [Código de ejemplo: diagramas de circuito](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
 
