---
description: Dada una lista de nombres de archivo completos, esta función los comprueba en la unidad local.
title: SccCheckout Function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 72d36ccaf5c6dcddb6730f52b0ce1c3074c605a7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904726"
---
# <a name="scccheckout-function"></a>Función SccCheckout
Dada una lista de nombres de archivo completos, esta función los comprueba en la unidad local. El comentario se aplica a todos los archivos que se están desprotegiendo. El argumento comment puede ser una `null` cadena.

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

[in] Estructura de contexto del complemento de control de código fuente.

 hWnd

[in] Identificador de la ventana del IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 nFiles

[in] Número de archivos seleccionados para su desprotegía.

 lpFileNames

[in] Matriz de nombres de ruta de acceso locales completos de archivos que se desprotegrán.

 lpComment

[in] Comentario que se va a aplicar a cada uno de los archivos seleccionados que se están desprotegiendo.

 fOptions

[in] Marcas de comandos (consulte [Marcas de bits usadas por comandos específicos).](../extensibility/bitflags-used-by-specific-commands.md)

 pvOptions

[in] Opciones específicas del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|La comprobación se ha realizado correctamente.|
|SCC_E_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|
|SCC_E_ACCESSFAILURE|Hubo un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_NONSPECIFICERROR|Error no específico. El archivo no se desprotegía.|
|SCC_E_ALREADYCHECKEDOUT|El usuario ya tiene el archivo desprotegiendo.|
|SCC_E_FILEISLOCKED|El archivo está bloqueado, lo que prohíbe la creación de nuevas versiones.|
|SCC_E_FILEOUTEXCLUSIVE|Otro usuario ha realizado una desprotección exclusiva en este archivo.|
|SCC_I_OPERATIONCANCELED|La operación se canceló antes de finalizar.|

## <a name="see-also"></a>Consulta también
- [Funciones de API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Bitflags usados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)
