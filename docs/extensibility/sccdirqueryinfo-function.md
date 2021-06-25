---
description: Esta función examina una lista de directorios completos para su estado actual.
title: Función SccDirQueryInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9a3e65fa03c7fc2b6a8ce83ba2bb39250547aadb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904622"
---
# <a name="sccdirqueryinfo-function"></a>Función SccDirQueryInfo
Esta función examina una lista de directorios completos para su estado actual.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccDirQueryInfo(
LPVOID  pContext,
LONG    nDirs,
LPCSTR* lpDirNames,
LPLONG  lpStatus
);
```

### <a name="parameters"></a>Parámetros
 pContext

[in] Estructura de contexto del complemento de control de código fuente.

 nDirs

[in] Número de directorios seleccionados para consultar.

 lpDirNames

[in] Matriz de rutas de acceso completas de los directorios que se consultarán.

 lpStatus

[in, out] Estructura de matriz para que el complemento de control de código fuente devuelva las marcas de estado (vea [Código de estado del directorio](../extensibility/directory-status-code-enumerator.md) para obtener más información).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|La consulta se ha realizado correctamente.|
|SCC_E_OPNOTSUPPORTED|El sistema de control de código fuente no admite esta operación.|
|SCC_E_ACCESSFAILURE|Hubo un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Error no específico.|

## <a name="remarks"></a>Observaciones
 La función rellena la matriz de devolución con una máscara de bits de bits de la familia (consulte El código de estado del directorio ), una entrada `SCC_DIRSTATUS` para cada directorio especificado. [](../extensibility/directory-status-code-enumerator.md) El autor de la llamada asigna la matriz de estado.

 El IDE usa esta función antes de cambiar el nombre de un directorio para comprobar si el directorio está bajo control de código fuente consultando si tiene un proyecto correspondiente. Si el directorio no está bajo control de código fuente, el IDE puede proporcionar la advertencia adecuada al usuario.

> [!NOTE]
> Si un complemento de control de código fuente decide no implementar uno o varios de los valores de estado, los bits no implementados deben establecerse en cero.

## <a name="see-also"></a>Consulta también
- [Funciones de API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Código de estado del directorio](../extensibility/directory-status-code-enumerator.md)
