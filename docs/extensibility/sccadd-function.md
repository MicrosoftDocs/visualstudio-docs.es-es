---
description: Esta función agrega nuevos archivos al sistema de control de código fuente.
title: SccAdd Function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7f73a91f7f801ca89a633f1722e0c4d1183fb3dc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904856"
---
# <a name="sccadd-function"></a>SccAdd (función)
Esta función agrega nuevos archivos al sistema de control de código fuente.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccAdd(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG*     pfOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parámetros
 pvContext

[in] Estructura de contexto del complemento de control de código fuente.

 hWnd

[in] Identificador de la ventana del IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 nFiles

[in] Número de archivos seleccionados que se van a agregar al proyecto actual tal y como se muestra en la `lpFileNames` matriz .

 lpFileNames

[in] Matriz de nombres locales completos de archivos que se van a agregar.

 lpComment

[in] Comentario que se va a aplicar a todos los archivos que se van a agregar.

 pfOptions

[in] Matriz de marcas de comandos, proporcionadas por archivo.

 pvOptions

[in] Opciones específicas del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|La operación de adición se ha realizado correctamente.|
|SCC_E_FILEALREADYEXISTS|El archivo seleccionado ya está bajo control de código fuente.|
|SCC_E_TYPENOTSUPPORTED|El tipo del archivo (por ejemplo, binario) no es compatible con el sistema de control de código fuente.|
|SCC_E_OPNOTSUPPORTED|El sistema de control de código fuente no admite esta operación.|
|SCC_E_ACCESSFAILURE|Hubo un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_NONSPECIFICERROR|Error no específico; Agregar no realizado.|
|SCC_I_OPERATIONCANCELED|La operación se canceló antes de finalizar.|
|SCC_I_RELOADFILE|Es necesario volver a cargar un archivo o proyecto.|
|SCC_E_FILENOTEXIST|No se encontró el archivo local.|

## <a name="remarks"></a>Observaciones
 Lo habitual `fOptions` se reemplaza aquí por una matriz, , con una `pfOptions` `LONG` especificación de opción por archivo. Esto se debe a que el tipo de archivo puede variar de un archivo a otro.

> [!NOTE]
> No es válido especificar las opciones y para el mismo archivo, pero no `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY` es válido especificar ninguna. El valor de ninguno es el mismo que el valor de , en cuyo caso el complemento de control de código fuente detecta automáticamente `SCC_FILETYPE_AUTO` el tipo de archivo.

 A continuación se muestra la lista de marcas usadas en la `pfOptions` matriz:

|Opción|Valor|Significado|
|------------|-----------|-------------|
|SCC_FILETYPE_AUTO|0x00|El complemento de control de código fuente debe detectar el tipo de archivo.|
|SCC_FILETYPE_TEXT|0x01|Indica un archivo de texto ASCII.|
|SCC_FILETYPE_BINARY|0x02|Indica un tipo de archivo distinto del texto ASCII.|
|SCC_ADD_STORELATEST|0x04|Almacena solo la copia más reciente del archivo, sin diferencias.|
|SCC_FILETYPE_TEXT_ANSI|0x08|Trata el archivo como texto ANSI.|
|SCC_FILETYPE_UTF8|0x10|Trata el archivo como texto Unicode en formato UTF8.|
|SCC_FILETYPE_UTF16LE|0x20|Trata el archivo como texto Unicode en formato UTF16 Little Endian.|
|SCC_FILETYPE_UTF16BE|0x40|Trata el archivo como texto Unicode en formato UTF16 Big Endian.|

## <a name="see-also"></a>Consulta también
- [Funciones de API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
