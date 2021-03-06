---
description: Esta función muestra las diferencias entre el directorio local actual en el disco del cliente y el proyecto correspondiente bajo control de código fuente.
title: Función SccDirDiff | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 98a843c061941765404397186af74ab71923a9da
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221605"
---
# <a name="sccdirdiff-function"></a>SccDirDiff función)
Esta función muestra las diferencias entre el directorio local actual en el disco del cliente y el proyecto correspondiente bajo control de código fuente.

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

de Estructura de contexto del complemento de control de código fuente.

 hWnd

de Identificador de la ventana del IDE que el complemento de control de código fuente puede utilizar como elemento primario para los cuadros de diálogo que proporciona.

 lpDirName

de Ruta de acceso completa al directorio local para el que se va a mostrar una diferencia visual.

 dwFlags

de Marcas de comandos (vea la sección comentarios).

 pvOptions

de Opciones específicas del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|El directorio del disco es el mismo que el del proyecto en el control de código fuente.|
|SCC_I_FILESDIFFER|El directorio del disco es diferente del proyecto en el control de código fuente.|
|SCC_I_RELOADFILE|Es necesario volver a cargar un archivo o proyecto.|
|SCC_E_FILENOTCONTROLLED|El directorio no está bajo el control de código fuente.|
|SCC_E_NOTAUTHORIZED|El usuario no tiene permiso para realizar esta operación.|
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Error no específico.|
|SCC_E_FILENOTEXIST|No se encontró el directorio local.|

## <a name="remarks"></a>Observaciones
 Esta función se usa para indicar al complemento de control de código fuente que muestre al usuario una lista de cambios en un directorio especificado. El complemento abre su propia ventana, en el formato que elija, para mostrar las diferencias entre el directorio del usuario en el disco y el proyecto correspondiente bajo control de versiones.

 Si un complemento admite la comparación de directorios, debe admitir la comparación de directorios en función del nombre de archivo, incluso si no se admiten las opciones de "comparación rápida".

|`dwFlags`|Interpretación|
|---------------|--------------------|
|SCC_DIFF_IGNORECASE|Comparación sin distinción entre mayúsculas y minúsculas (se puede usar para diferencias rápidas u objetos visuales).|
|SCC_DIFF_IGNORESPACE|Omite el espacio en blanco (se puede usar para las diferencias rápidas o visuales).|
|SCC_DIFF_QD_CONTENTS|Si es compatible con el complemento de control de código fuente, compara de forma silenciosa el directorio, byte por byte.|
|SCC_DIFF_QD_CHECKSUM|Si es compatible con el complemento, compara de forma silenciosa el directorio a través de una suma de comprobación o, si no se admite, recurre a SCC_DIFF_QD_CONTENTS.|
|SCC_DIFF_QD_TIME|Si es compatible con el complemento, compara de forma silenciosa el directorio a través de su marca de tiempo, o bien, si no se admite, recurre a SCC_DIFF_QD_CHECKSUM o SCC_DIFF_QD_CONTENTS.|

> [!NOTE]
> Esta función utiliza las mismas marcas de comando que [SccDiff](../extensibility/sccdiff-function.md). Sin embargo, un complemento de control de código fuente puede optar por no admitir la operación "comparación rápida" para los directorios.

## <a name="see-also"></a>Consulte también
- [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
