---
title: Función SccCheckin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d8a5a91a0300f256b66970403a3431edf0fe757e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189532"
---
# <a name="scccheckin-function"></a>SccCheckin (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función protege los archivos desprotegidos previamente en el sistema de control de código fuente, almacenando los cambios y creando una nueva versión. Se llama a esta función con un recuento y una matriz de nombres de los archivos que se van a proteger.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 de Estructura de contexto del complemento de control de código fuente.  
  
 hWnd  
 de Identificador de la ventana del IDE que el complemento SCC puede utilizar como elemento primario para los cuadros de diálogo que proporciona.  
  
 N archivos  
 de Número de archivos seleccionados que se van a proteger.  
  
 lpFileNames  
 de Matriz de nombres de ruta de acceso local completa de los archivos que se van a proteger.  
  
 lpComment  
 de Comentario que se va a aplicar a cada uno de los archivos seleccionados que se van a proteger. Es `NULL` si el complemento de control de código fuente debe solicitar un comentario.  
  
 Opciones  
 de Marcas de comandos, ya sea 0 o `SCC_KEEP_CHECKEDOUT` .  
  
 pvOptions  
 de Opciones específicas del complemento SCC.  
  
## <a name="return-value"></a>Valor devuelto  
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:  
  
|Value|Descripción|  
|-----------|-----------------|  
|SCC_OK|Los archivos se protegieron correctamente.|  
|SCC_E_FILENOTCONTROLLED|El archivo seleccionado no está bajo el control de código fuente.|  
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC_E_NONSPECIFICERROR|Error no específico. No se protegió el archivo.|  
|SCC_E_NOTCHECKEDOUT|El usuario no ha desprotegido el archivo, por lo que no puede protegerlo.|  
|SCC_E_CHECKINCONFLICT|No se pudo realizar la protección porque:<br /><br /> -Otro usuario ha protegido de antemano y `bAutoReconcile` era false.<br /><br /> o bien<br /><br /> : No se puede realizar la combinación automática (por ejemplo, cuando los archivos son binarios).|  
|SCC_E_VERIFYMERGE|El archivo se combinó automáticamente, pero no se protegió en la comprobación de usuario pendiente.|  
|SCC_E_FIXMERGE|El archivo se ha fusionado mediante combinación automática, pero no se ha protegido debido a un conflicto de fusión mediante combinación que se debe resolver manualmente.|  
|SCC_E_NOTAUTHORIZED|El usuario no tiene permiso para realizar esta operación.|  
|SCC_I_OPERATIONCANCELED|La operación se canceló antes de completarse.|  
|SCC_I_RELOADFILE|Es necesario volver a cargar un archivo o proyecto.|  
|SCC_E_FILENOTEXIST|No se encontró el archivo local.|  
  
## <a name="remarks"></a>Observaciones  
 El comentario se aplica a todos los archivos que se protegen. El argumento comment puede ser una `null` cadena, en cuyo caso el complemento de control de código fuente puede solicitar al usuario una cadena de comentario para cada archivo.  
  
 El `fOptions` argumento puede tener un valor de la `SCC_KEEP_CHECKEDOUT` marca para indicar la intención del usuario para comprobar el archivo y desprotegerlo de nuevo.  
  
## <a name="see-also"></a>Consulte también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
