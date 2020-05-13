---
title: Función SccCheckout (SccCheckout) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ed809e33a80bf2903c88550e97b28b1e0178bcd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701106"
---
# <a name="scccheckout-function"></a>Función SccCheckout
Dada una lista de nombres de archivo completos, esta función los desprotege en la unidad local. El comentario se aplica a todos los archivos que se están desprotegiendo. El argumento comment `null` puede ser una cadena.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccCheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parámetros
 pvContext

[en] La estructura de contexto del complemento de control de código fuente.

 hWnd

[en] Identificador de la ventana IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 nArchivos

[en] Número de archivos seleccionados para ser desprotegidos.

 lpFileNames

[en] Matriz de nombres de ruta local completos de los archivos que se van a desproteger.

 lpComment

[en] Comentario que se aplicará a cada uno de los archivos seleccionados que se van a desproteger.

 fOptions

[en] Marcas de comandos (consulte [Bitflags utilizados por comandos específicos).](../extensibility/bitflags-used-by-specific-commands.md)

 pvOptions

[en] Opciones específicas del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|La salida tuvo éxito.|
|SCC_E_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|
|SCC_E_ACCESSFAILURE|Se ha producido un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_NONSPECIFICERROR|Fallo inespecífico. El archivo no se ha traído.|
|SCC_E_ALREADYCHECKEDOUT|El usuario ya tiene el archivo desprotegido.|
|SCC_E_FILEISLOCKED|El archivo está bloqueado, lo que prohíbe la creación de nuevas versiones.|
|SCC_E_FILEOUTEXCLUSIVE|Otro usuario ha realizado una desprotección exclusiva en este archivo.|
|SCC_I_OPERATIONCANCELED|La operación se canceló antes de la finalización.|

## <a name="see-also"></a>Vea también
- [Funciones de API de plug-in de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Bitflags utilizados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)
