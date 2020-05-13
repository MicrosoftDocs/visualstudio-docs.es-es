---
title: Función SccDirDiff ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1bb592a1174a91480ed76ef818733c288c5273c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701013"
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

[en] La estructura de contexto del complemento de control de código fuente.

 hWnd

[en] Identificador de la ventana IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 lpDirName

[en] Ruta de acceso completa al directorio local para el que se muestra una diferencia visual.

 dwFlags

[en] Indicadores de comando (consulte la sección Comentarios).

 pvOptions

[en] Opciones específicas del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|El directorio del disco es el mismo que el proyecto en el control de código fuente.|
|SCC_I_FILESDIFFER|El directorio del disco es diferente del proyecto en el control de código fuente.|
|SCC_I_RELOADFILE|Es necesario volver a cargar un archivo o proyecto.|
|SCC_E_FILENOTCONTROLLED|El directorio no está bajo control de código fuente.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_ACCESSFAILURE|Se ha producido un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Fallo inespecífico.|
|SCC_E_FILENOTEXIST|No se pudo encontrar el directorio local.|

## <a name="remarks"></a>Observaciones
 Esta función se utiliza para indicar al complemento de control de código fuente que muestre al usuario una lista de cambios en un directorio especificado. El complemento abre su propia ventana, en un formato de su elección, para mostrar las diferencias entre el directorio del usuario en el disco y el proyecto correspondiente bajo control de versión.

 Si un complemento admite la comparación de directorios en absoluto, debe admitir la comparación de directorios en una base de nombre de archivo, incluso si no se admiten las opciones "quick-diff".

|`dwFlags`|Interpretación|
|---------------|--------------------|
|SCC_DIFF_IGNORECASE|Comparación sin distinción entre mayúsculas y minúsculas (se puede utilizar para diferencias rápidas o visuales).|
|SCC_DIFF_IGNORESPACE|Ignora el espacio en blanco (se puede utilizar para difusión rápida o visual).|
|SCC_DIFF_QD_CONTENTS|Si es compatible con el complemento de control de código fuente, compara silenciosamente el directorio, byte a byte.|
|SCC_DIFF_QD_CHECKSUM|Si es compatible con el complemento, compara de forma silenciosa el directorio a través de una suma de comprobación o, si no se admite, vuelve a SCC_DIFF_QD_CONTENTS.|
|SCC_DIFF_QD_TIME|Si es compatible con el complemento, compara de forma silenciosa el directorio a través de su marca de tiempo o, si no se admite, recae en SCC_DIFF_QD_CHECKSUM o SCC_DIFF_QD_CONTENTS.|

> [!NOTE]
> Esta función utiliza los mismos indicadores de comando que [SccDiff](../extensibility/sccdiff-function.md). Sin embargo, un complemento de control de código fuente puede optar por no admitir la operación "quick-diff" para directorios.

## <a name="see-also"></a>Vea también
- [Funciones de API de plug-in de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
