---
title: ¿Qué&#39;s nuevo en el origen de controlar la API del complemento versión 1.3 | Microsoft Docs
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
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 58756bde7f3eb9fbc0f42bf494d82e8cc508796e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793926"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>¿Qué&#39;s nuevo en el origen de controlar la API del complemento versión 1.3
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La API de complemento de Control de origen de la versión 1.3 presenta las siguientes funciones nuevas para proporcionar un control más avanzado.  
  
## <a name="changes"></a>Cambios  
 Las funciones siguientes son nuevas para la API de complemento de Control de origen de la versión 1.3:  
  
|Función|Información general|  
|--------------|--------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Permite que los bits de capacidad adicional que se informe|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Permite examinar los archivos que tienen las versiones más recientes en la base de control de versión que en el disco local|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Permite examinar el estado de los cambios de nombre (cambios de nombre, adiciones y eliminaciones) para los archivos especificados|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Permite el examen de directorios y archivos en la base de datos de control de versión|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Agrega una lista de archivos especificada desde la base de datos de control de versión para el proyecto actual|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Realiza un silencioso "Get" de los archivos especificados (no se muestra ninguna interfaz de usuario)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Permite el acceso a opciones específicas del usuario|  
  
## <a name="see-also"></a>Vea también  
 [Introducción](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

