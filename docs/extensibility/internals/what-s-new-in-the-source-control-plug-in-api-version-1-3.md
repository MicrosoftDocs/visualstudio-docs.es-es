---
title: Novedades &apos; de la API del complemento de control de código fuente 1,3
description: Obtenga información sobre las novedades de la API del complemento de control de código fuente versión 1,3, que presenta las nuevas funciones para proporcionar un control más avanzado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7ab9079248931758efbcfcd792ce3c79ccffb270
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074267"
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
