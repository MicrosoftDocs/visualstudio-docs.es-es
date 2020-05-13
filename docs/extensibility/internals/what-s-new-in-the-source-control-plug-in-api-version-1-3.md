---
title: Qué&#39;s New en la versión 1.3 de la API de complemento de Control de código fuente Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9654f1f3ae6d4a3d73ddc3afca2977a57a98297d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703359"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Qué&#39;s Nuevo en la versión 1.3 de la API de complemento de Control de código fuente
La versión 1.3 de la API de complemento de Control de código fuente presenta las siguientes funciones nuevas para proporcionar un control más avanzado.

## <a name="changes"></a>Cambios
 Las siguientes funciones son nuevas en la versión 1.3 de la API de complemento de Control de código fuente:

|Función|Información general|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Permite notificar bits de capacidad adicionales|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Permite el examen de archivos que tienen versiones más recientes en la base de datos de control de versiones que en el disco local|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Permite examinar el estado de los cambios de nombre (renombrar, adiciones y eliminaciones) para los archivos especificados|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Permite el examen de directorios y archivos en la base de datos de control de versiones|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Agrega una lista especificada de archivos de la base de datos de control de versiones al proyecto actual|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Realiza un "Get" silencioso de los archivos especificados (no se muestra ninguna interfaz de usuario)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Permite el acceso a opciones específicas del usuario|

## <a name="see-also"></a>Vea también
- [Introducción](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
