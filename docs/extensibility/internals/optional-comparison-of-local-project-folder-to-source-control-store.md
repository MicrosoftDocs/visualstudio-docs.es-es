---
title: Comparar la carpeta del proyecto con el almacén de control de código fuente ( Source Control Store) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: facb3b656e0ac50b50fdb0291307aa2fe98b1df4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706861"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Comparación opcional de la carpeta de proyecto local con el almacén de control de código fuente
En Source Control Plug-in API 1.2, la comparación entre la carpeta del proyecto local y el control de código fuente se realiza mediante las funciones [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) y [SccDirDiff](../../extensibility/sccdirdiff-function.md).

 En el **Explorador**de soluciones , si se selecciona una carpeta en lugar de un archivo individual, el menú contextual **Comparar versiones** invoca el nuevo [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) y [SccDirDiff](../../extensibility/sccdirdiff-function.md) en el complemento de control de código fuente.

## <a name="new-capability-flags"></a>Nuevos indicadores de capacidad
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>Funciones nuevas
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 Se `SccDirQueryInfo` llama a `SccDirDiff` la función antes para determinar si el directorio de trabajo está controlado por código fuente. La `SccDirDiff` función muestra las diferencias entre el directorio local actual y la carpeta de control de código fuente correspondiente. Este comando solicita al complemento de control de código fuente que muestre la lista de cambios en el directorio. Un complemento de control de código fuente proporciona su propia interfaz de usuario para mostrar las diferencias.

> [!NOTE]
> Esta función utiliza los mismos indicadores de comando [que SccDiff](../../extensibility/sccdiff-function.md). Como proveedor de complementos de control de código fuente, puede optar por no admitir la operación "diff rápida" para directorios.

## <a name="see-also"></a>Vea también
- [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
