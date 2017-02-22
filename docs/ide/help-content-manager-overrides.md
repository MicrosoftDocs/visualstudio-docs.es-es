---
title: "Invalidaciones de Help Content Manager | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Invalidaciones de Help Content Manager
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El Registro se puede modificar para cambiar el comportamiento predeterminado del Visor de Ayuda y las características relacionadas con la Ayuda en el IDE de Visual Studio.  
  
|Tarea|Clave del Registro|Valor y definición|  
|-----------|------------------------|------------------------|  
|Definir un extremo de servicio único|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VSWinExpress\\14.0\\Help|NewContentAndUpdateService\-\-*HTTPValueForTheServiceEndpoint*.|  
|Definir el valor predeterminado En línea o Sin conexión|HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VSWinExpress\\14.0\\help|UseOnlineHelp: escriba `0` para especificar Ayuda local y escriba `1` para especificar Ayuda en línea.|  
|Definir un extremo F1 único|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VSWinExpress\\14.0\\Help|OnlineBaseUrl\-\-*HTTPValueForTheServiceEndpoint*|  
|Invalidar la prioridad de trabajos del servicio BITS|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node \(en un equipo de 64 bits\)\\Microsoft\\Help\\v2.2|BITSPriority: use uno de los valores siguientes: **foreground**, **high**, **normal** o **low**.|  
|Deshabilitar En línea \(y la opción IDE en línea\)|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node \(en un equipo de 64 bits\)\\Microsoft\\VisualStudio\\14.0\\Help|OnlineHelpPreferenceDisabled: establézcalo en 1 para deshabilitar el acceso al contenido de Ayuda en línea.|  
|Deshabilitar Administrar contenido|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node \(en un equipo de 64 bits\)\\Microsoft\\VisualStudio\\14.0\\Help|ContentManagementDisabled: establézcalo en 1 para deshabilitar la pestaña **Administrar contenido** del Visor de Ayuda.|  
|Apuntar al almacén de contenido local en un recurso compartido de red|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Help\\v2.2\\Catalogs\\VisualStudio11|LocationPath\=”*ContentStoreNetworkShare*”|  
|Deshabilitar la instalación de contenido en el primer inicio de la característica de Visual Studio.|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node \(en un equipo de 64 bits\)\\Microsoft\\VisualStudio\\14.0\\Help|DisableFirstRunHelpSelection: establézcalo en 1 para deshabilitar las características de ayuda que se configuran la primera vez que se inicia Visual Studio.|  
  
## Vea también  
 [Guía del administrador del Visor de Ayuda](../ide/help-viewer-administrator-guide.md)