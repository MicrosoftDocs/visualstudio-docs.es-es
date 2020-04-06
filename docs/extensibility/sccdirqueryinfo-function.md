---
title: Función SccDirQueryInfo ( SccDirQueryInfo) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 222b5d15a1e2bcd9bd3f27a5cd0e9904642d9786
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700949"
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

[en] La estructura de contexto del complemento de control de código fuente.

 nDirs

[en] El número de directorios seleccionados para ser consultados.

 lpDirNames

[en] Matriz de rutas de acceso completas de los directorios que se van a consultar.

 lpStatus

[adentro, fuera] Una estructura de matriz para el complemento de control de código fuente para devolver los indicadores de estado (consulte Código de estado de [directorio](../extensibility/directory-status-code-enumerator.md) para obtener más información).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|La consulta se realizó correctamente.|
|SCC_E_OPNOTSUPPORTED|El sistema de control de código fuente no admite esta operación.|
|SCC_E_ACCESSFAILURE|Se ha producido un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Fallo inespecífico.|

## <a name="remarks"></a>Observaciones
 La función rellena la matriz return con `SCC_DIRSTATUS` una máscara de bits de bits de la familia (consulte Código de estado de [directorio),](../extensibility/directory-status-code-enumerator.md)una entrada para cada directorio dado. El autor de la llamada asigna la matriz de estado.

 El IDE usa esta función antes de cambiar el nombre de un directorio para comprobar si el directorio está bajo control de código fuente consultando si tiene un proyecto correspondiente. Si el directorio no está bajo control de código fuente, el IDE puede proporcionar la advertencia adecuada al usuario.

> [!NOTE]
> Si un complemento de control de código fuente elige no implementar uno o varios de los valores de estado, los bits no implementados deben establecerse en cero.

## <a name="see-also"></a>Vea también
- [Funciones de API de plug-in de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Código de estado del directorio](../extensibility/directory-status-code-enumerator.md)
