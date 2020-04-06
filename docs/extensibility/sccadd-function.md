---
title: Función SccAdd (SccAdd) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 23a6226b0d3cc2441a509c16b2e4672a766f3329
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701310"
---
# <a name="sccadd-function"></a>Función SccAdd
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

[en] La estructura de contexto del complemento de control de código fuente.

 hWnd

[en] Identificador de la ventana IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 nArchivos

[en] Número de archivos seleccionados para agregarse al `lpFileNames` proyecto actual como se indica en la matriz.

 lpFileNames

[en] Matriz de nombres locales completos de los archivos que se van a agregar.

 lpComment

[en] El comentario que se aplicará a todos los archivos que se van a agregar.

 pfOptions

[en] Matriz de indicadores de comando, proporcionados por archivo.

 pvOptions

[en] Opciones específicas del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|La operación de adición se realizó correctamente.|
|SCC_E_FILEALREADYEXISTS|El archivo seleccionado ya está bajo control de código fuente.|
|SCC_E_TYPENOTSUPPORTED|El tipo del archivo (por ejemplo, binario) no es compatible con el sistema de control de código fuente.|
|SCC_E_OPNOTSUPPORTED|El sistema de control de código fuente no admite esta operación.|
|SCC_E_ACCESSFAILURE|Se ha producido un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_NONSPECIFICERROR|Error inespecífico; añadir no realizado.|
|SCC_I_OPERATIONCANCELED|La operación se canceló antes de la finalización.|
|SCC_I_RELOADFILE|Es necesario volver a cargar un archivo o proyecto.|
|SCC_E_FILENOTEXIST|No se encontró el archivo local.|

## <a name="remarks"></a>Observaciones
 Los `fOptions` habituales se reemplazan aquí `pfOptions`por `LONG` una matriz, con una especificación de opción por archivo. Esto se debe a que el tipo de archivo puede variar de un archivo a un archivo.

> [!NOTE]
> No es válido `SCC_FILETYPE_TEXT` especificar `SCC_FILETYPE_BINARY` ambas opciones y opciones para el mismo archivo, pero no es válido especificar ninguna. Establecer ninguno es lo `SCC_FILETYPE_AUTO`mismo que establecer , en cuyo caso el complemento de control de código fuente detecta automáticamente el tipo de archivo.

 A continuación se muestra la `pfOptions` lista de indicadores utilizados en la matriz:

|Opción|Value|Significado|
|------------|-----------|-------------|
|SCC_FILETYPE_AUTO|0x00|El complemento de control de código fuente debe detectar el tipo de archivo.|
|SCC_FILETYPE_TEXT|0x01|Indica un archivo de texto ASCII.|
|SCC_FILETYPE_BINARY|0x02|Indica un tipo de archivo distinto del texto ASCII.|
|SCC_ADD_STORELATEST|0x04|Almacena solo la copia más reciente del archivo, sin deltas.|
|SCC_FILETYPE_TEXT_ANSI|0x08|Trata el archivo como texto ANSI.|
|SCC_FILETYPE_UTF8|0x10|Trata el archivo como texto Unicode en formato UTF8.|
|SCC_FILETYPE_UTF16LE|0x20|Trata el archivo como texto Unicode en formato UTF16 Little Endian.|
|SCC_FILETYPE_UTF16BE|0x40|Trata el archivo como texto Unicode en formato UTF16 Big Endian.|

## <a name="see-also"></a>Vea también
- [Funciones de API de plug-in de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
