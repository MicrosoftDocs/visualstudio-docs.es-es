---
title: Controladores de eventos propagan cambios fuera del modelo | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
ms.assetid: 0ac8d1e4-239f-4370-ba1d-3769bb38b8a5
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 24ef57b545360cccbf75039b5f64a0f53e636dd8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60059908"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Los controladores de eventos propagan cambios fuera del modelo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En el SDK de modelado y visualización, puede definir controladores de eventos de almacén para propagar los cambios a los recursos fuera de la tienda, como las variables no-store, archivos, los modelos en otros almacenes, o en otros [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extensiones. Store los controladores de eventos se ejecutan después del final de la transacción en el que se ha producido el evento desencadenador. También se ejecutan en una operación de deshacer o rehacer. Por lo tanto, a diferencia del almacén de reglas, los eventos de almacén son muy útiles para actualizar los valores que están fuera de la tienda. A diferencia de los eventos. NET, almacén de controladores de eventos se registran para que escuche en una clase: no es necesario que registrar un controlador independiente para cada instancia. Para obtener más información sobre cómo elegir entre diferentes formas de controlar los cambios, consulte [responde a y propagar los cambios](../modeling/responding-to-and-propagating-changes.md).  
  
 La superficie gráfica y otros controles de interfaz de usuario son ejemplos de recursos externos que pueden controlarse mediante el almacén de eventos.  
  
### <a name="to-define-a-store-event"></a>Para definir un evento de almacén  
  
1. Elija el tipo de evento que desea supervisar. Para obtener una lista completa, examine las propiedades de <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>. Cada propiedad se corresponde con un tipo de evento. Usado con mayor frecuencia son tipos de evento:  
  
   - `ElementAdded` : se desencadena cuando un elemento de modelo, se crea el vínculo de relación, forma o conector.  
  
   - La ElementPropertyChanged: se desencadena cuando el valor de un `Normal` se cambia la propiedad de dominio. El evento se desencadena únicamente si los valores nuevos y antiguos no son iguales. El evento no se puede aplicar a las propiedades de almacenamiento calculadas y personalizadas.  
  
        No se puede aplicar a las propiedades de rol que se corresponden con los vínculos de relación. En su lugar, use `ElementAdded` para supervisar la relación de dominio.  
  
   - `ElementDeleted` : se desencadena después de un elemento de modelo, relación, forma o conector se ha eliminado. Todavía puede tener acceso a los valores de propiedad del elemento, pero no tendrá ninguna relación con otros elementos.  
  
2. Agregue una definición de clase parcial para _Sudsl_**DocData** en un archivo de código independiente en el **DslPackage** proyecto.  
  
3. Escribir el código del evento como un método, como en el ejemplo siguiente. Puede ser `static`, a menos que desee tener acceso a `DocData`.  
  
4. Invalidar `OnDocumentLoaded()` para registrar el controlador. Si tiene más de un controlador, puede registrarlos todos en el mismo lugar.  
  
   La ubicación del código de registro no es crítica. `DocView.LoadView()` es una ubicación alternativa.  
  
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
      base.OnDocumentLoaded(); // Don’t forget this.  
  
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
  
## <a name="using-events-to-make-undoable-adjustments-in-the-store"></a>Uso de eventos para realizar ajustes que se pueden deshacer en el Store  
 Eventos de Store no se utilizan normalmente para propagar los cambios en el almacén, porque el controlador de eventos que se ejecuta una vez confirmada la transacción. En su lugar, se usaría una regla del almacén. Para obtener más información, consulte [propagar cambios en el modelo de reglas de](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Sin embargo, podría usar un controlador de eventos para realizar actualizaciones adicionales en el almacén, si desea que el usuario para poder deshacer las actualizaciones adicionales por separado desde el evento original. Por ejemplo, suponga que los caracteres en minúsculas son la convención habitual para títulos de álbumes. Puede escribir un controlador de eventos de almacén que corrige el título a minúsculas después de que el usuario ha escrito en mayúsculas. Pero el usuario podría utilizar el comando Deshacer para cancelar la corrección de la restauración de los caracteres en mayúsculas. Deshará eliminaría el cambio del usuario.  
  
 Por el contrario, si ha escrito una regla de almacén para hacer lo mismo, el cambio del usuario y su corrección sería en la misma transacción, para que el usuario no pudo deshacer el ajuste sin perder el cambio original.  
  
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
  
 Si escribe un evento que se actualiza el almacén:  
  
- Use `store.InUndoRedoOrRollback` para evitar realizar cambios en los elementos del modelo en la fase de reversión. El Administrador de transacciones todo lo establecerá en el almacén a su estado original.  
  
- Use `store.InSerializationTransaction` para evitar realizar cambios mientras se carga el modelo del archivo.  
  
- Hará que los cambios aún más los eventos que se desencadene. Asegúrese de que se evite un bucle infinito.  
  
## <a name="store-event-types"></a>Tipos de evento de Store  
 Cada tipo de evento corresponde a una colección en Store.EventManagerDirectory. Puede agregar o quitar controladores de eventos en cualquier momento, pero resulta habitual para agregarlos al cargar el documento.  
  
|`EventManagerDirectory` Nombre de propiedad|Se ejecuta cuando|  
|-------------------------------------------|-------------------|  
|ElementAdded|Se crea una instancia de una clase de dominio, relación de dominio, forma, conector o diagrama.|  
|ElementDeleted|Un elemento de modelo se ha quitado de directorio de elementos de la tienda y ya no es el origen o destino de cualquier relación. El elemento no se elimina realmente de la memoria, pero se conserva en el caso de una operación de deshacer futuras.|  
|ElementEventsBegun|Se invoca al final de una transacción exterior.|  
|ElementEventsEnded|Se invoca cuando se han procesado todos los demás eventos.|  
|ElementMoved|Un elemento de modelo se ha movido desde un almacén de partición a otra.<br /><br /> Esto no está relacionado con la ubicación de una forma del diagrama.|  
|ElementPropertyChanged|El valor de una propiedad de dominio ha cambiado. Esto solo se ejecuta si los valores antiguos y nuevos no son iguales.|  
|RolePlayerChanged|Uno de los dos roles (extremos) de una relación hace referencia a un nuevo elemento.|  
|RolePlayerOrderChanged|En un rol con multiplicidad es mayor que 1, ha cambiado la secuencia de vínculos.|  
|TransactionBeginning||  
|TransactionCommitted||  
|TransactionRolledBack||  
  
## <a name="see-also"></a>Vea también  
 [Responder a los cambios y propagarlos](../modeling/responding-to-and-propagating-changes.md)   
 [Código de ejemplo: Diagramas de circuitos](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
