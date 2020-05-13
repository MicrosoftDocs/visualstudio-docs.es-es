---
title: Función SccUncheckout (SccUncheckout) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4317133b2f215e0f9af447e5c042785561231f63
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700248"
---
# <a name="sccuncheckout-function"></a>SccUncheckout (Función)
Esta función deshace una operación de desprotección anterior, restaurando así el contenido del archivo o archivos seleccionados al estado anterior a la desprotección. Se pierden todos los cambios realizados en el archivo desde la desprotección.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccUncheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Parámetros
 pvContext

[en] La estructura de contexto del complemento de control de código fuente.

 hWnd

[en] Identificador de la ventana IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 nArchivos

[en] Número de archivos especificados en la `lpFileNames` matriz.

 lpFileNames

[en] Matriz de nombres de ruta de acceso local completos de archivos para los que deshacer una desprotección.

 fOptions

[en] Marcas de comando (no utilizadas).

 pvOptions

[en] Opciones específicas del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|Deshacer checkout fue exitoso.|
|SCC_E_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|
|SCC_E_ACCESSFAILURE|Se ha producido un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_NONSPECIFICERROR|Fallo inespecífico. Deshacer la salida no se realizó correctamente.|
|SCC_E_NOTCHECKEDOUT|El usuario no tiene el archivo desprotegido.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_PROJNOTOPEN|El proyecto no se ha abierto desde el control de código fuente.|
|SCC_I_OPERATIONCANCELED|La operación se canceló antes de la finalización.|

## <a name="remarks"></a>Observaciones
 Después de `SCC_STATUS_CHECKEDOUT` esta `SCC_STATUS_MODIFIED` operación, los indicadores y se borrarán para los archivos en los que se realizó la desprotección de deshacer.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
