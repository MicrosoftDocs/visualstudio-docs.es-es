---
description: Esta función elimina archivos del sistema de control de código fuente.
title: SccRemove Function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f4a608b3556040033d9f51535ad29d0abf5d4e35
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904131"
---
# <a name="sccremove-function"></a>SccRemove (Función)
Esta función elimina archivos del sistema de control de código fuente.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccRemove(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Parámetros
 pvContext

[in] Estructura de contexto del complemento de control de código fuente.

 hWnd

[in] Identificador de la ventana del IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 nFiles

[in] Número de archivos especificados en la `lpFileNames` matriz.

 lpFileNames

[in] Matriz de nombres de ruta de acceso locales completos de los archivos que se quitarán.

 lpComment

[in] Comentario que se va a aplicar a cada archivo que se va a quitar.

 fOptions

[in] Marcas de comandos (sin usar).

 pvOptions

[in] Opciones específicas del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|La eliminación se ha realizado correctamente.|
|SCC_E_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|
|SCC_E_OPNOTSUPPORTED|El sistema de control de código fuente no admite esta operación.|
|SCC_E_ISCHECKEDOUT|No se puede quitar un archivo porque un usuario lo tiene desprotegiendo.|
|SCC_E_ACCESSFAILURE|Hubo un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_NONSPECIFICERROR|Error no específico; No se quitó el archivo .|
|SCC_I_OPERATIONCANCELED|La operación se canceló antes de finalizar.|

## <a name="remarks"></a>Observaciones
 Esta función quita los archivos del sistema de control de código fuente, pero no los elimina del disco duro local del usuario.

## <a name="see-also"></a>Consulta también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
