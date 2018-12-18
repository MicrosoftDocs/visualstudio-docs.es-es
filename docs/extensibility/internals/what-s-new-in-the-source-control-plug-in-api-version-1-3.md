---
title: ¿Qué&#39;s nuevos en el origen de controlar la versión de API de complemento 1.3 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: abeb2a0a936a5d706e2e3744e9dd0f4e3123bdbf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31145014"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>¿Qué&#39;s nuevos en el origen de controlar la versión de API de complemento 1.3
La API de complementos de Control de origen de la versión 1.3 presenta las siguientes nuevas funciones para proporcionar un control más avanzado.  
  
## <a name="changes"></a>Cambios  
 Las funciones siguientes son Novedades de la API de complementos de Control de origen de la versión 1.3:  
  
|Función|Información general|  
|--------------|--------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Permite que los bits de una capacidad adicional que se informe|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Permite realizar el examen de los archivos que tienen versiones más recientes en la versión control base de datos que en el disco local|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Permite examinar el estado de los cambios de nombre (cambia el nombre, adiciones y eliminaciones) para los archivos especificados|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Permite realizar el examen de directorios y archivos en la base de datos de control de versión|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Agrega una lista especificada de los archivos de la base de datos de control de versión para el proyecto actual|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Realiza un silenciosa "Get" de los archivos especificados (no se muestra ninguna interfaz de usuario)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Permite el acceso a opciones específicas del usuario|  
  
## <a name="see-also"></a>Vea también  
 [Introducción](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)