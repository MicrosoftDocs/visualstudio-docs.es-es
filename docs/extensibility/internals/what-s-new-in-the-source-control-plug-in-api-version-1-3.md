---
title: "Novedades de la API de complemento de origen Control versi&#243;n 1.3 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "control de código fuente plug-ins, novedades de API v1.3"
  - "Novedades [Visual Studio SDK], origen control complementos nuevos."
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Novedades de la API de complemento de origen Control versi&#243;n 1.3
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La versión 1,3 de la API del complemento de control de código fuente presenta las nuevas funciones siguientes para proporcionar más control avanzado.  
  
## Cambios  
 Las funciones siguientes son nuevos en la versión 1,3 de la API del complemento de control de código fuente:  
  
|Función|Información general|  
|-------------|-------------------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Permite que los bits adicionales de capacidad se van|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Permite la inspección de los archivos que tienen versiones más recientes de la base de datos de control de versiones que en el disco local|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Permite la inspección del estado de cambios de nombre \(rename, las adiciones, y eliminación\) para los archivos especificados|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Permite el examen de directorios y archivos de la base de datos de control de versiones|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Agrega una lista de archivos especificada de la base de datos de control de versiones al proyecto actual|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Realiza un silencioso “get” de los archivos especificados \(no se muestra ninguna interfaz de usuario\)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Permite el acceso a las opciones específicas|  
  
## Vea también  
 [Introducción](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [Novedades de la API de complemento de origen Control versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)