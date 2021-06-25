---
description: Esta función comprueba los archivos previamente desprotegiendo en el sistema de control de código fuente, almacenando los cambios y creando una nueva versión.
title: SccCheckin Function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d324c03096df5178decd6f6954928df3f2c6b9aa
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904752"
---
# <a name="scccheckin-function"></a>Función SccCheckin
Esta función comprueba los archivos previamente desprotegiendo en el sistema de control de código fuente, almacenando los cambios y creando una nueva versión. Se llama a esta función con un recuento y una matriz de nombres de los archivos que se va a comprobar.

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

[in] Estructura de contexto del complemento de control de código fuente.

 hWnd

[in] Identificador de la ventana del IDE que el complemento SCC puede usar como elemento primario para los cuadros de diálogo que proporciona.

 nFiles

[in] Número de archivos seleccionados para la desprotegción.

 lpFileNames

[in] Matriz de nombres de ruta de acceso locales completos de los archivos que se va a comprobar.

 lpComment

[in] Comentario que se va a aplicar a cada uno de los archivos seleccionados que se están registrando. Este parámetro es `NULL` si el complemento de control de código fuente debe solicitar un comentario.

 fOptions

[in] Marcas de comandos, 0 o `SCC_KEEP_CHECKEDOUT` .

 pvOptions

[in] Opciones específicas del complemento SCC.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|El archivo se ha registrado correctamente.|
|SCC_E_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|
|SCC_E_ACCESSFAILURE|Hubo un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_NONSPECIFICERROR|Error no específico. El archivo no se ha registrado.|
|SCC_E_NOTCHECKEDOUT|El usuario no ha desprotegiendo el archivo, por lo que no puede comprobarlo.|
|SCC_E_CHECKINCONFLICT|No se pudo realizar la comprobación porque:<br /><br /> - Otro usuario se ha registrado con antelación y `bAutoReconcile` era false.<br /><br /> O bien<br /><br /> - No se puede realizar la combinación automática (por ejemplo, cuando los archivos son binarios).|
|SCC_E_VERIFYMERGE|El archivo se ha combinado automáticamente, pero no se ha registrado en la comprobación del usuario pendiente.|
|SCC_E_FIXMERGE|El archivo se ha combinado automáticamente, pero no se ha registrado debido a un conflicto de combinación que se debe resolver manualmente.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_I_OPERATIONCANCELED|La operación se canceló antes de completarse.|
|SCC_I_RELOADFILE|Es necesario volver a cargar un archivo o proyecto.|
|SCC_E_FILENOTEXIST|No se encontró el archivo local.|

## <a name="remarks"></a>Observaciones
 El comentario se aplica a todos los archivos que se están registrando. El argumento comment puede ser una cadena, en cuyo caso el complemento de control de código fuente puede solicitar al usuario una cadena `null` de comentario para cada archivo.

 Al argumento se le puede dar un valor de la marca para indicar la intención del usuario de comprobar el archivo y `fOptions` volver a `SCC_KEEP_CHECKEDOUT` comprobarlo.

## <a name="see-also"></a>Consulta también
- [Funciones de API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
