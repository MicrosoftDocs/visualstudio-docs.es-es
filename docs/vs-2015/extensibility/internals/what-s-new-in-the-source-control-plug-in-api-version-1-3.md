---
title: Novedades de las&#39;de la API del complemento de control de código fuente versión 1,3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d5333a5b44e9c990843e66da357578e4a90d210
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200930"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>&#39;novedades de la API del complemento de control de código fuente 1,3
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La API del complemento de control de código fuente versión 1,3 presenta las siguientes funciones nuevas para proporcionar un control más avanzado.  
  
## <a name="changes"></a>Cambios  
 Las siguientes funciones son nuevas en la API del complemento de control de código fuente versión 1,3:  
  
|Función|Información general|  
|--------------|--------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Permite que se notifiquen bits de capacidad adicionales.|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Permite examinar los archivos que tienen versiones más recientes en la base de datos de control de versiones que en el disco local.|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Permite examinar el estado de los cambios de nombre (nombres, adiciones y eliminaciones) de los archivos especificados.|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Permite el examen de directorios y archivos en la base de datos de control de versiones.|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Agrega una lista especificada de archivos de la base de datos de control de versiones al proyecto actual.|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Realiza una "obtención" silenciosa de los archivos especificados (no se muestra ninguna interfaz de usuario)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Permite el acceso a opciones específicas del usuario|  
  
## <a name="see-also"></a>Consulte también  
 [Introducción](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
