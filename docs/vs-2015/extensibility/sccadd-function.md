---
title: SccAdd (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 52fa4f40b64ce345f3f5a376bdeba258e81ea09a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49233566"
---
# <a name="sccadd-function"></a>SccAdd (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función agrega nuevos archivos al sistema de control de código fuente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
  
#### <a name="parameters"></a>Parámetros  
 pvContext  
 [in] La estructura de contexto de complemento de control de origen.  
  
 hWnd  
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como un elemento primario para los cuadros de diálogo que proporciona.  
  
 n  
 [in] Número de archivos que se van a agregarse al proyecto actual como se indica en la `lpFileNames` matriz.  
  
 lpFileNames  
 [in] Matriz de nombres locales completos de archivos que se va a agregarse.  
  
 lpComment  
 [in] El comentario que se aplicará a todos los archivos que se va a agregar.  
  
 pfOptions  
 [in] Matriz de marcas de comando, proporcionado en una base por archivo.  
  
 pvOptions  
 [in] Opciones de específicas del complemento de control de código fuente.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|La operación de agregar fue correcta.|  
|SCC_E_FILEALREADYEXISTS|El archivo seleccionado ya está bajo control de código fuente.|  
|SCC_E_TYPENOTSUPPORTED|El tipo de archivo (por ejemplo, binario) no es compatible con el sistema de control de código fuente.|  
|SCC_E_OPNOTSUPPORTED|El sistema de control de código fuente no admite esta operación.|  
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso el sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC_E_NONSPECIFICERROR|Error no específico; agregar no realizó.|  
|SCC_I_OPERATIONCANCELED|La operación se canceló antes de completarse.|  
|SCC_I_RELOADFILE|Debe volver a cargar un archivo o proyecto.|  
|SCC_E_FILENOTEXIST|No se encontró el archivo local.|  
  
## <a name="remarks"></a>Comentarios  
 El habitual `fOptions` se reemplazan aquí por una matriz, `pfOptions`, con una `LONG` opción especificación por archivo. Esto es porque el tipo de archivo puede variar de un archivo a.  
  
> [!NOTE]
>  No es válido especificar ambos `SCC_FILETYPE_TEXT` y `SCC_FILETYPE_BINARY` opciones para el mismo archivo, pero es válido especificar ninguno. Establecer ninguna de ellas es lo mismo que establecer `SCC_FILETYPE_AUTO`, en cuyo caso el origen de controlar el complemento detecta automáticamente el tipo de archivo.  
  
 Esta es la lista de marcas usadas en el `pfOptions` matriz:  
  
|Opción|Valor|Significado|  
|------------|-----------|-------------|  
|SCC_FILETYPE_AUTO|0 x 00|El complemento de control de origen debe detectar el tipo de archivo.|  
|SCC_FILETYPE_TEXT|0 x 01|Indica un archivo de texto ASCII.|  
|SCC_FILETYPE_BINARY|0 x 02|Indica un tipo de archivo que no sea texto ASCII.|  
|SCC_ADD_STORELATEST|0x04|Almacena sólo la última copia del archivo, no hay diferencias.|  
|SCC_FILETYPE_TEXT_ANSI|0 x 08|Trata el archivo como texto ANSI.|  
|SCC_FILETYPE_UTF8|0 x 10|Trata el archivo como texto Unicode en formato UTF8.|  
|SCC_FILETYPE_UTF16LE|0 x 20|Trata el archivo como texto Unicode en UTF16 Little Endian formato.|  
|SCC_FILETYPE_UTF16BE|0x40|Trata el archivo como texto Unicode en UTF16 Big Endian de formato.|  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)

