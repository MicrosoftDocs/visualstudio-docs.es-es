---
title: Obtener acceso a la configuración de fuente y color almacenada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fbb2f118d903eae2124e705f14c7aa7b51bf9c4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821839"
---
# <a name="accessing-stored-font-and-color-settings"></a>Acceso a la configuración de fuentes y colores almacenados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] entorno de desarrollo integrado (IDE) almacena la configuración modificada para fuentes y colores en el registro. Puede usar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz para tener acceso a esta configuración.  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Para iniciar la persistencia de estado de fuentes y colores  
 La información de fuente y color se almacena por Categoría en la siguiente ubicación del registro: [HKCU\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ *\<CategoryGUID>* ], donde *\<CategoryGUID>* es el GUID de la categoría.  
  
 Por lo tanto, para iniciar la persistencia, un VSPackage debe:  
  
- Obtenga una <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz llamando al `QueryService` proveedor de servicios global.  
  
     `QueryService` se debe llamar a con un argumento de ID. de servicio de `SID_SVsFontAndColorStorage` y un argumento de identificador de interfaz de `IID_IVsFontAndColorStorage` .  
  
- Use el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> método para abrir una categoría que se va a conservar utilizando el GUID de la categoría y una marca de modo como argumentos.  
  
  El modo, especificado por el `fFlags` argumento, se construye a partir de los valores de la <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> enumeración. Este modo controla:  

  - La configuración a la que se puede tener acceso a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz.  

  - Todas las configuraciones o solo las que los usuarios modifican y que se pueden recuperar a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz.  

  - La manera de propagar los cambios a la configuración del usuario.  

  - Formato de los valores de color que se utilizan.  

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Para usar la persistencia de estado de fuentes y colores  
 La persistencia de fuentes y colores implica:  
  
- Sincronizar la configuración del IDE con la configuración almacenada en el registro.  
  
- Propagando información de modificación del registro.  
  
- Establecer y recuperar la configuración almacenada en el registro.  
  
  La sincronización de la configuración de almacenamiento con la configuración del IDE es en gran medida transparente. El IDE subyacente escribe automáticamente la configuración actualizada para **Mostrar los elementos** en las entradas del registro de las categorías.  
  
  Si varios VSPackages comparten una categoría determinada, un VSPackage debe requerir que se generen eventos cuando se utilicen métodos de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz para modificar la configuración del registro almacenada.  
  
  De forma predeterminada, la generación de eventos no está habilitada. Para habilitar la generación de eventos, se debe abrir una categoría mediante <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> . Esto hace que el IDE llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> método adecuado que implementa un VSPackage.  
  
> [!NOTE]
> Las modificaciones realizadas a través de la página de propiedades **fuente y color** generan eventos independientes de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> . Puede usar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfaz para determinar si es necesaria una actualización de la configuración de fuente y color almacenada en caché antes de llamar a los métodos de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> clase.  
  
### <a name="storing-and-retrieving-information"></a>Almacenar y recuperar información  
 Para obtener o configurar la información que un usuario puede modificar para un elemento de presentación con nombre en una categoría abierta, los VSPackages llaman a los <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> métodos y.  
  
 La información sobre los atributos de fuente para una categoría determinada se obtiene mediante los <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> métodos y.  
  
> [!NOTE]
> El `fFlags` argumento que se pasa al <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> método cuando se abre esa categoría define el comportamiento de los <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> métodos y. De forma predeterminada, estos métodos solo devuelven información aboutdisplay itemsthat han cambiado. Sin embargo, si se abre una categoría mediante la <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> marca, y pueden tener acceso a los elementos de presentación actualizados y sin modificar <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> .  
  
 De forma predeterminada, solo la información de **elementos de presentación** cambiada se guarda en el registro. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>No se puede usar la interfaz para recuperar toda la configuración de fuentes y colores.  
  
> [!NOTE]
> Los <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> métodos y <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> devuelven REGDB_E_KEYMISSING, (0x80040152L) cuando se usan para recuperar información sobre **los elementos de presentación**no modificados.  
  
 La configuración de todos los **elementos de presentación** de una **categoría** determinada se puede obtener mediante los métodos de la `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` interfaz.  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [Implementación de categorías y elementos para mostrar personalizados](../extensibility/implementing-custom-categories-and-display-items.md)
