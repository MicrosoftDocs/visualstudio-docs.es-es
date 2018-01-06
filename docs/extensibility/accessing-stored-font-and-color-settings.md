---
title: "Obtener acceso a la configuración de Color y fuente almacenado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e4dec66fca6061601c4bc02389605d140ee3bb81
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-stored-font-and-color-settings"></a>Obtener acceso a la configuración de Color y fuente almacenado
El [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE) almacena la configuración modificada para fuentes y colores en el registro. Puede usar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz para tener acceso a esta configuración.  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Para iniciar la persistencia de los Estados de fuentes y colores  
 Información de fuente y color se almacena por categoría en la siguiente ubicación del registro: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\<versión de Visual Studio >*\FontAndColors\\  *\<CategoryGUID >*], donde  *\<CategoryGUID >* es el identificador GUID de categoría.  
  
 Por lo tanto, para iniciar la persistencia, un VSPackage debe:  
  
-   Obtener un <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz mediante una llamada a `QueryService` con el proveedor de servicios globales.  
  
     `QueryService`se debe llamar mediante el uso de un argumento de Id. de servicio `SID_SVsFontAndColorStorage` y un argumento de Id. de interfaz `IID_IVsFontAndColorStorage`.  
  
-   Use la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> método para abrir una categoría para conservar mediante el GUID de la categoría y un indicador de modo como argumentos.  
  
     El modo, especificado por el `fFlags` argumento, se construye a partir de valores en el <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> enumeración. Controles de este modo:  
  
    -   La configuración que se puede tener acceso a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz.  
  
    -   Todas las configuraciones o solo los que los usuarios modificar y que se pueden recuperar a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz.  
  
    -   La manera de propagar los cambios a la configuración de usuario.  
  
    -   El formato de valores de color que se usan.  
  
## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Con la persistencia de estado de uso de fuentes y colores  
 Colores y fuentes persistencia implica:  
  
-   Sincronizar la configuración de IDE con la configuración almacenada en el registro.  
  
-   Propagación de la información de modificación del registro.  
  
-   Establecer y recuperar la configuración almacenada en el registro.  
  
 Sincronizar la configuración de almacenamiento con la configuración de IDE es en gran medida transparente. El IDE subyacente escribe automáticamente la configuración actualizada para **elementos para mostrar** a las entradas del registro de categorías.  
  
 Si varios paquetes VSPackage comparte una categoría determinada, un VSPackage debe requerir que los eventos se generan cuando métodos de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz sirven para modificar la configuración del registro almacenado.  
  
 De forma predeterminada, no está habilitada la generación de eventos. Para habilitar la generación de eventos, debe abrirse una categoría mediante el uso de <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>. Esto hace que el IDE llamar a la correspondiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> método que implementa un paquete VSPackage.  
  
> [!NOTE]
>  Las modificaciones a través de la **fuente y Color** página de propiedades Generar eventos independientes de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>. Puede usar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfaz para determinar si se necesita una actualización de configuración de fuente y color almacenados en memoria caché antes de llamar a los métodos de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> clase.  
  
### <a name="storing-and-retrieving-information"></a>Almacenar y recuperar información  
 Para obtener o configurar la información que un usuario puede modificar para un elemento de visualización con nombre en una categoría abierto, llame VSPackages el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> métodos.  
  
 Atributos de información acerca de la fuente para una categoría determinada se obtiene mediante el uso de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> métodos.  
  
> [!NOTE]
>  El `fFlags` argumento que se pasa a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> método cuando se abre esa categoría define el comportamiento de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> métodos. De forma predeterminada, estos itemsthat aboutdisplay de devolver únicamente información de métodos han cambiado. Sin embargo, si se abre una categoría mediante el <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> marca, ambos actualizado y mostrar sin modificar los elementos son accesibles por <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>.  
  
 De forma predeterminada, solo cambiar **elementos para mostrar** información se guarda en el registro. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz no se puede usar para recuperar toda la configuración de fuentes y colores.  
  
> [!NOTE]
>  El <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> métodos devuelven REGDB_E_KEYMISSING, (0x80040152L) cuando se usan para recuperar información acerca de sin cambios **elementos para mostrar**.  
  
 La configuración de todos los **elementos para mostrar** en un determinado **categoría** puede obtenerse mediante el uso de los métodos de la `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` interfaz.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [Implementación de categorías personalizadas y mostrar los elementos](../extensibility/implementing-custom-categories-and-display-items.md)