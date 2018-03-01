---
title: "Función SccCheckin | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f95377f79d02952c63b673d50569fac058a8573c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="scccheckin-function"></a>SccCheckin (función)
Esta función comprueba en archivos previamente desprotegido en el sistema de control de código fuente, almacenar los cambios y crear una nueva versión. Esta función se invoca con un recuento y una matriz de nombres de los archivos pueda protegerse.  
  
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
  
#### <a name="parameters"></a>Parámetros  
 pvContext  
 [in] La estructura de contexto de complemento de control de código fuente.  
  
 hWnd  
 [in] Identificador de la ventana del IDE que puede usar el complemento control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 nFiles  
 [in] Número de archivos seleccionados pueda protegerse.  
  
 lpFileNames  
 [in] Matriz de nombres de ruta de acceso local completa de archivos pueda protegerse.  
  
 lpComment  
 [in] Comentario que se aplicará a cada uno de los archivos seleccionados que se protege. Se trata de `NULL` si el complemento de control de código fuente debe solicitar un comentario.  
  
 fOptions  
 [in] Marcas de comando, 0 o `SCC_KEEP_CHECKEDOUT`.  
  
 pvOptions  
 [in] Opciones específicas del complemento de control de código fuente.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Los archivos se comprobó correctamente.|  
|SCC_E_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|  
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC_E_NONSPECIFICERROR|Error no determinado. El archivo no se ha protegido.|  
|SCC_E_NOTCHECKEDOUT|El usuario no ha desprotegido el archivo, por lo que no puede protegerlo.|  
|SCC_E_CHECKINCONFLICT|No se pudo realizar la protección porque:<br /><br /> -Otro usuario ha protegido con antelación y `bAutoReconcile` fuese falsa.<br /><br /> O bien<br /><br /> -La combinación automática no se puede realizar (por ejemplo, si los archivos son binarios).|  
|SCC_E_VERIFYMERGE|Archivo ha sido combinada automáticamente pero no se ha comprobado pendiente de comprobación del usuario.|  
|SCC_E_FIXMERGE|Archivo ha sido combinada automáticamente pero no se ha comprobado debido a un conflicto de combinación que se debe resolver manualmente.|  
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC_I_OPERATIONCANCELED|Se canceló la operación antes de la finalización.|  
|SCC_I_RELOADFILE|Debe volver a cargar un archivo o proyecto.|  
|SCC_E_FILENOTEXIST|No se encontró el archivo local.|  
  
## <a name="remarks"></a>Comentarios  
 El comentario se aplica a todos los archivos que se protege. El argumento de comentario puede ser un `null` de cadena, en cuyo caso el complemento de control de código fuente puede pedir al usuario una cadena de comentario para cada archivo.  
  
 El `fOptions` argumento puede indicarse un valor de la `SCC_KEEP_CHECKEDOUT` marca para indicar que la intención del usuario para proteger el archivo y volver a desprotegerlo.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)