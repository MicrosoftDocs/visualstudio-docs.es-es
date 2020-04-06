---
title: Función SccCheckin (SccCheckin) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5ba512642e1a63d9d39856f96194d717583d44f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701184"
---
# <a name="scccheckin-function"></a>Función SccCheckin
Esta función comprueba los archivos previamente desprotegidos en el sistema de control de código fuente, almacenando los cambios y creando una nueva versión. Esta función se llama con un recuento y una matriz de nombres de los archivos que se van a proteger.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccCheckin (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPSTR*    lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parámetros
 pvContext

[en] La estructura de contexto del complemento de control de código fuente.

 hWnd

[en] Identificador de la ventana IDE que el complemento SCC puede usar como elemento primario para los cuadros de diálogo que proporciona.

 nArchivos

[en] Número de archivos seleccionados para registrarse.

 lpFileNames

[en] Matriz de nombres de ruta local completos de los archivos que se van a proteger.

 lpComment

[en] Comentario que se aplicará a cada uno de los archivos seleccionados que se van a registrar. Este parámetro `NULL` es si el complemento de control de código fuente debe solicitar un comentario.

 fOptions

[en] Marcas de comando, `SCC_KEEP_CHECKEDOUT`0 o .

 pvOptions

[en] Opciones específicas del complemento SCC.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|El archivo se ha registrado correctamente.|
|SCC_E_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|
|SCC_E_ACCESSFAILURE|Se ha producido un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_NONSPECIFICERROR|Fallo inespecífico. El archivo no se registró.|
|SCC_E_NOTCHECKEDOUT|El usuario no ha traído el archivo, por lo que no puede registrarlo.|
|SCC_E_CHECKINCONFLICT|No se pudo realizar el registro porque:<br /><br /> - Otro usuario se `bAutoReconcile` ha registrado por delante y era falso.<br /><br /> o bien<br /><br /> - La fusión automática no se puede hacer (por ejemplo, cuando los archivos son binarios).|
|SCC_E_VERIFYMERGE|El archivo se ha fusionado automáticamente, pero no se ha registrado en pendiente de verificación del usuario.|
|SCC_E_FIXMERGE|El archivo se ha fusionado automáticamente, pero no se ha registrado debido a un conflicto de combinación que debe resolverse manualmente.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_I_OPERATIONCANCELED|La operación se canceló antes de la finalización.|
|SCC_I_RELOADFILE|Es necesario volver a cargar un archivo o proyecto.|
|SCC_E_FILENOTEXIST|No se encontró el archivo local.|

## <a name="remarks"></a>Observaciones
 El comentario se aplica a todos los archivos que se están protegiendo. El argumento comment `null` puede ser una cadena, en cuyo caso el complemento de control de código fuente puede solicitar al usuario una cadena de comentario para cada archivo.

 Al `fOptions` argumento se le puede `SCC_KEEP_CHECKEDOUT` dar un valor de la marca para indicar la intención del usuario de proteger el archivo y volver a desprotegerlo.

## <a name="see-also"></a>Vea también
- [Funciones de API de plug-in de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
