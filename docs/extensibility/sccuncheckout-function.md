---
description: Esta función deshace una operación de desprotección anterior, con lo que se restaura el contenido del archivo o archivos seleccionados al estado anterior a la desprotección.
title: Función SccUncheckout | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 33e0c4904a92d71e000d8c911d551eb8d0aab621
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221358"
---
# <a name="sccuncheckout-function"></a>SccUncheckout (Función)
Esta función deshace una operación de desprotección anterior, con lo que se restaura el contenido del archivo o archivos seleccionados al estado anterior a la desprotección. Se pierden todos los cambios realizados en el archivo desde la desprotección.

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

de Estructura de contexto del complemento de control de código fuente.

 hWnd

de Identificador de la ventana del IDE que el complemento de control de código fuente puede utilizar como elemento primario para los cuadros de diálogo que proporciona.

 N archivos

de Número de archivos especificados en la `lpFileNames` matriz.

 lpFileNames

de Matriz de nombres de ruta de acceso local completa de los archivos para los que se va a deshacer una desprotección.

 Opciones

de Marcas de comandos (no utilizadas).

 pvOptions

de Opciones específicas del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Deshacer desprotección realizada correctamente.|
|SCC_E_FILENOTCONTROLLED|El archivo seleccionado no está bajo el control de código fuente.|
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|
|SCC_E_NONSPECIFICERROR|Error no específico. No se pudo deshacer la desprotección.|
|SCC_E_NOTCHECKEDOUT|El usuario no tiene el archivo desprotegido.|
|SCC_E_NOTAUTHORIZED|El usuario no tiene permiso para realizar esta operación.|
|SCC_E_PROJNOTOPEN|El proyecto no se ha abierto desde el control de código fuente.|
|SCC_I_OPERATIONCANCELED|La operación se canceló antes de completarse.|

## <a name="remarks"></a>Observaciones
 Después de esta operación, `SCC_STATUS_CHECKEDOUT` se `SCC_STATUS_MODIFIED` borrarán las marcas y para los archivos en los que se realizó la desprotección de deshacer.

## <a name="see-also"></a>Consulte también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
