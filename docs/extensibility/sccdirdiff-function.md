---
description: Esta función muestra las diferencias entre el directorio local actual en el disco cliente y el proyecto correspondiente bajo control de código fuente.
title: SccDirDiff Function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e938cdaedf8541d787673371cfce3d07e005711f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904648"
---
# <a name="sccdirdiff-function"></a>Función SccDirDiff
Esta función muestra las diferencias entre el directorio local actual en el disco cliente y el proyecto correspondiente bajo control de código fuente.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccDirDiff(
   LPVOID    pContext,
   HWND      hWnd,
   LPCSTR    lpDirName,
   LONG      dwFlags,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parámetros
 pContext

[in] Estructura de contexto del complemento de control de código fuente.

 hWnd

[in] Identificador de la ventana del IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 lpDirName

[in] Ruta de acceso completa al directorio local para el que se va a mostrar una diferencia visual.

 dwFlags

[in] Marcas de comandos (consulte la sección Comentarios).

 pvOptions

[in] Opciones específicas del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|El directorio del disco es el mismo que el proyecto en el control de código fuente.|
|SCC_I_FILESDIFFER|El directorio del disco es diferente del proyecto en el control de código fuente.|
|SCC_I_RELOADFILE|Es necesario volver a cargar un archivo o proyecto.|
|SCC_E_FILENOTCONTROLLED|El directorio no está bajo control de código fuente.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_ACCESSFAILURE|Hubo un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Error no específico.|
|SCC_E_FILENOTEXIST|No se encontró el directorio local.|

## <a name="remarks"></a>Observaciones
 Esta función se usa para indicar al complemento de control de código fuente que muestre al usuario una lista de cambios en un directorio especificado. El complemento abre su propia ventana, en un formato de su elección, para mostrar las diferencias entre el directorio del usuario en el disco y el proyecto correspondiente bajo control de versiones.

 Si un complemento admite la comparación de directorios, debe admitir la comparación de directorios en función del nombre de archivo, incluso si no se admiten las opciones de "diferencia rápida".

|`dwFlags`|Interpretación|
|---------------|--------------------|
|SCC_DIFF_IGNORECASE|Comparación sin diferencias entre mayúsculas y minúsculas (se puede usar para diferencias rápidas o para objetos visuales).|
|SCC_DIFF_IGNORESPACE|Omite el espacio en blanco (se puede usar para la diferencia rápida o el objeto visual).|
|SCC_DIFF_QD_CONTENTS|Si es compatible con el complemento de control de código fuente, compara de forma silenciosa el directorio, byte por byte.|
|SCC_DIFF_QD_CHECKSUM|Si es compatible con el complemento, compara de forma silenciosa el directorio a través de una suma de comprobación o, si no se admite, vuelve a SCC_DIFF_QD_CONTENTS.|
|SCC_DIFF_QD_TIME|Si es compatible con el complemento, compara de forma silenciosa el directorio a través de su marca de tiempo o, si no se admite, vuelve a SCC_DIFF_QD_CHECKSUM o SCC_DIFF_QD_CONTENTS.|

> [!NOTE]
> Esta función usa las mismas marcas de comandos que [SccDiff](../extensibility/sccdiff-function.md). Sin embargo, un complemento de control de código fuente puede optar por no admitir la operación de "diferencia rápida" para directorios.

## <a name="see-also"></a>Consulta también
- [Funciones de API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
