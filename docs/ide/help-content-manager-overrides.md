---
title: Invalidaciones de Help Content Manager | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-help-viewer
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: c4889d40e9ca53cccf7de384e609eb959d8981f5
ms.contentlocale: es-es
ms.lasthandoff: 05/13/2017

---
# <a name="help-content-manager-overrides"></a>Invalidaciones de Help Content Manager
El Registro se puede modificar para cambiar el comportamiento predeterminado del Visor de Ayuda y las características relacionadas con la Ayuda en el IDE de Visual Studio.  
  
|Tarea|Clave del Registro|Valor y definición|  
|----------|------------------|--------------------------|  
|Definir un extremo de servicio único|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|NewContentAndUpdateService: *HTTPValueForTheServiceEndpoint*.|  
|Definir el valor predeterminado En línea o Sin conexión|HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help|UseOnlineHelp: escriba `0` para especificar Ayuda local y escriba `1` para especificar Ayuda en línea.|  
|Definir un extremo F1 único|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|OnlineBaseUrl: *HTTPValueForTheServiceEndpoint*|  
|Invalidar la prioridad de trabajos del servicio BITS|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (en un equipo de 64 bits)\Microsoft\Help\v2.2|BITSPriority: use uno de los valores siguientes: **foreground**, **high**, **normal** o **low**.|  
|Deshabilitar En línea (y la opción IDE en línea)|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (en un equipo de 64 bits)\Microsoft\VisualStudio\14.0\Help|OnlineHelpPreferenceDisabled: establézcalo en 1 para deshabilitar el acceso al contenido de Ayuda en línea.|  
|Deshabilitar Administrar contenido|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (en un equipo de 64 bits)\Microsoft\VisualStudio\14.0\Help|ContentManagementDisabled: establézcalo en 1 para deshabilitar la pestaña **Administrar contenido** del Visor de Ayuda.|  
|Apuntar al almacén de contenido local en un recurso compartido de red|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio11|LocationPath="*ContentStoreNetworkShare*"|  
|Deshabilitar la instalación de contenido en el primer inicio de la característica de Visual Studio.|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (en un equipo de 64 bits)\Microsoft\VisualStudio\14.0\Help|DisableFirstRunHelpSelection: establézcalo en 1 para deshabilitar las características de ayuda que se configuran la primera vez que se inicia Visual Studio.|  
  
## <a name="see-also"></a>Vea también  
 [Guía del administrador del Visor de Ayuda](../ide/help-viewer-administrator-guide.md)
