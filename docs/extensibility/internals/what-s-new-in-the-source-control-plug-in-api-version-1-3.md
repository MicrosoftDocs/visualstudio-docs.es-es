---
title: Novedades &apos; de la API del complemento de control de código fuente versión 1,3 | Microsoft Docs
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
ms.openlocfilehash: ec24e9ee3079d3b02ac13759b6ab5bdee8c07a84
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2020
ms.locfileid: "88706456"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>&#39;novedades de la API del complemento de control de código fuente 1,3
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
- [Introducción](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
