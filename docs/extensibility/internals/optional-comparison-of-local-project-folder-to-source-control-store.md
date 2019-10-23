---
title: Comparar la carpeta del proyecto con el almacén de control de código fuente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 45bd5b105a2fd24078bc85d8cf5b044351cd78be
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726127"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Comparación opcional de la carpeta de proyecto local con el almacén de control de código fuente
En la API de complemento de control de código fuente 1,2, la comparación entre la carpeta de proyecto local y el control de código fuente se realiza mediante las funciones [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) y [SccDirDiff](../../extensibility/sccdirdiff-function.md).

 En **Explorador de soluciones**, si se selecciona una carpeta en lugar de un archivo individual, el menú contextual **Comparar versiones** invoca las nuevas [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) y [SccDirDiff](../../extensibility/sccdirdiff-function.md) en el complemento de control de código fuente.

## <a name="new-capability-flags"></a>Nuevas marcas de capacidad
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>Nuevas funciones
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 Se llama a la función `SccDirQueryInfo` antes de `SccDirDiff` para determinar si el directorio de trabajo está controlado por código fuente. La función `SccDirDiff` muestra las diferencias entre el directorio local actual y la carpeta de control de código fuente correspondiente. Este comando pide al complemento de control de código fuente que muestre la lista de cambios en el directorio. Un complemento de control de código fuente proporciona su propia interfaz de usuario para mostrar las diferencias.

> [!NOTE]
> Esta función utiliza las mismas marcas de comando que [SccDiff](../../extensibility/sccdiff-function.md). Como proveedor de complementos de control de código fuente, puede optar por no admitir la operación "diferencia rápida" en los directorios.

## <a name="see-also"></a>Vea también
- [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)