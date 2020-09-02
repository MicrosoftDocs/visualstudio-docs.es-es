---
title: Función SccAdd | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701310"
---
# <a name="sccadd-function"></a>SccAdd función)
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

de Estructura de contexto del complemento de control de código fuente.

 hWnd

de Identificador de la ventana del IDE que el complemento de control de código fuente puede utilizar como elemento primario para los cuadros de diálogo que proporciona.

 N archivos

de Número de archivos seleccionados que se van a agregar al proyecto actual, tal como se indica en la `lpFileNames` matriz.

 lpFileNames

de Matriz de nombres locales completos de los archivos que se van a agregar.

 lpComment

de Comentario que se va a aplicar a todos los archivos que se van a agregar.

 pfOptions

de Matriz de marcas de comandos, que se proporciona en cada archivo.

 pvOptions

de Opciones específicas del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|La operación de agregar se realizó correctamente.|
|SCC_E_FILEALREADYEXISTS|El archivo seleccionado ya está bajo control de código fuente.|
|SCC_E_TYPENOTSUPPORTED|El sistema de control de código fuente no admite el tipo de archivo (por ejemplo, binario).|
|SCC_E_OPNOTSUPPORTED|El sistema de control de código fuente no admite esta operación.|
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|
|SCC_E_NOTAUTHORIZED|El usuario no tiene permiso para realizar esta operación.|
|SCC_E_NONSPECIFICERROR|Error no específico; no se ha realizado la adición.|
|SCC_I_OPERATIONCANCELED|La operación se canceló antes de completarse.|
|SCC_I_RELOADFILE|Es necesario volver a cargar un archivo o proyecto.|
|SCC_E_FILENOTEXIST|No se encontró el archivo local.|

## <a name="remarks"></a>Observaciones
 Normalmente, `fOptions` se reemplaza aquí por una matriz, `pfOptions` , con una `LONG` especificación de opción por archivo. Esto se debe a que el tipo de archivo puede variar de un archivo a un archivo.

> [!NOTE]
> No es válido especificar `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY` las opciones y para el mismo archivo, pero es válido especificar ninguno. Establecer ninguno es igual que el valor `SCC_FILETYPE_AUTO` de configuración, en cuyo caso el complemento de control de código fuente detecta automáticamente el tipo de archivo.

 A continuación se muestra la lista de marcas usadas en la `pfOptions` matriz:

|Opción|Value|Significado|
|------------|-----------|-------------|
|SCC_FILETYPE_AUTO|0x00|El complemento de control de código fuente debe detectar el tipo de archivo.|
|SCC_FILETYPE_TEXT|0x01|Indica un archivo de texto ASCII.|
|SCC_FILETYPE_BINARY|0x02|Indica un tipo de archivo distinto de texto ASCII.|
|SCC_ADD_STORELATEST|0x04|Almacena solo la última copia del archivo, sin diferencias.|
|SCC_FILETYPE_TEXT_ANSI|0x08|Trata el archivo como texto ANSI.|
|SCC_FILETYPE_UTF8|0x10|Trata el archivo como texto Unicode en formato UTF8.|
|SCC_FILETYPE_UTF16LE|0x20|Trata el archivo como texto Unicode en formato UTF16 Little Endian.|
|SCC_FILETYPE_UTF16BE|0x40|Trata el archivo como texto Unicode en formato UTF16 Big Endian.|

## <a name="see-also"></a>Vea también
- [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
