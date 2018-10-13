---
title: Obtener acceso a la configuración de Color y fuente almacenado | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8179262ceabe1765ee6c9eab96553bcbcbbee419
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49191404"
---
# <a name="accessing-stored-font-and-color-settings"></a>Obtener acceso a la configuración de Color y fuente almacenado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] el entorno de desarrollo integrado (IDE) almacena la configuración modificada para fuentes y colores en el registro. Puede usar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz para tener acceso a estos valores.  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Para iniciar la persistencia de los Estados de fuentes y colores  
 Se almacena la información de fuente y color por categoría en la siguiente ubicación del registro: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\<versión de Visual Studio >* \FontAndColors\\  *\<CategoryGUID >*], donde  *\<CategoryGUID >* es el GUID de categoría.  
  
 Por lo tanto, para iniciar la persistencia, un VSPackage debe:  
  
-   Obtener un <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz mediante una llamada a `QueryService` con el proveedor de servicios global.  
  
     `QueryService` debe llamarse mediante el uso de un argumento de Id. de servicio `SID_SVsFontAndColorStorage` y un argumento de Id. de interfaz `IID_IVsFontAndColorStorage`.  
  
-   Use el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> método para abrir una categoría que se deben conservar mediante el uso GUID de la categoría y un indicador de modo como argumentos.  
  
     El modo, especificado por el `fFlags` argumento, se construye a partir de valores en el <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> enumeración. Controles de este modo:  
  
    -   La configuración que se puede acceder a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz.  
  
    -   Todas las configuraciones o solo aquellos que los usuarios modificar y que se pueden recuperar a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz.  
  
    -   La manera de propagar los cambios a la configuración de usuario.  
  
    -   El formato de valores de color que se usan.  
  
## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Persistencia de estado de uso de fuentes y colores  
 Colores y fuentes de persistencia implica:  
  
-   Sincronizando la configuración del IDE con configuración almacenada en el registro.  
  
-   Propagación de la información de modificación del registro.  
  
-   Establecer y recuperar la configuración almacenada en el registro.  
  
 Sincronizar la configuración de almacenamiento con la configuración del IDE es en gran medida transparente. El IDE subyacente escribe automáticamente la configuración actualizada para **mostrar los elementos** a las entradas del registro de categorías.  
  
 Si varios VSPackages comparten una categoría determinada, un VSPackage debe requerir que se generan eventos cuando los métodos de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz sirven para modificar la configuración del registro almacenado.  
  
 De forma predeterminada, no está habilitada la generación de eventos. Para habilitar la generación de eventos, se debe abrir una categoría mediante el uso de <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>. Esto hace que el IDE llamar a la correspondiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> método que implementa un paquete VSPackage.  
  
> [!NOTE]
>  Las modificaciones realizadas con la **fuente y Color** página de propiedades generan eventos independientes de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>. Puede usar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfaz para determinar si se necesita una actualización de la configuración de fuente y color almacenada en caché antes de llamar a los métodos de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> clase.  
  
### <a name="storing-and-retrieving-information"></a>Almacenar y recuperar información  
 Para obtener o configurar la información que un usuario puede modificar para un elemento de presentación con nombre en una categoría abierta, llame los VSPackages la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> métodos.  
  
 Atributos de información acerca de la fuente para una categoría determinada se obtiene con el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> métodos.  
  
> [!NOTE]
>  El `fFlags` argumento que se pasa a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> método cuando se abre esa categoría define el comportamiento de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> métodos. De forma predeterminada, estos itemsthat aboutdisplay de devolver únicamente información de los métodos han cambiado. Sin embargo, si se abre una categoría mediante el <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> marca, ambos actualizado y mostrar sin modificar los elementos puede tener acceso a <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>.  
  
 De forma predeterminada, solo puede cambiar **elementos para mostrar** información se conserva en el registro. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz no se puede usar para recuperar toda la configuración de fuentes y colores.  
  
> [!NOTE]
>  El <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> métodos devuelven REGDB_E_KEYMISSING, (0x80040152L) cuando se usan para recuperar información sobre sin cambios **mostrar los elementos**.  
  
 La configuración de todos los **elementos para mostrar** en un determinado **categoría** puede obtenerse mediante el uso de los métodos de la `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` interfaz.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [Implementación de categorías y elementos para mostrar personalizados](../extensibility/implementing-custom-categories-and-display-items.md)

