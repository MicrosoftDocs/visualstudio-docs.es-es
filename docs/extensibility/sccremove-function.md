---
title: SccRemove (función) | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4db8360f6874f8e2c506aefb153c663670fa5cba
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55014840"
---
# <a name="sccremove-function"></a>SccRemove (Función)
Esta función elimina los archivos del sistema de control de código fuente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccRemove(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pvContext  
 [in] La estructura de contexto de complemento de control de origen.  
  
 hWnd  
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como un elemento primario para los cuadros de diálogo que proporciona.  
  
 nFiles  
 [in] Número de archivos especificados en el `lpFileNames` matriz.  
  
 lpFileNames  
 [in] Matriz de nombres de ruta de acceso local completa de archivos que se va a quitar.  
  
 lpComment  
 [in] El comentario que se aplicará a cada archivo que se va a quitar.  
  
 Opciones  
 [in] Marcas de comando (sin usar).  
  
 pvOptions  
 [in] Opciones de específicas del complemento de control de código fuente.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Eliminación fue correcta.|  
|SCC_E_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|  
|SCC_E_OPNOTSUPPORTED|El sistema de control de código fuente no admite esta operación.|  
|SCC_E_ISCHECKEDOUT|No se puede quitar un archivo porque un usuario actualmente tiene desprotegido.|  
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso el sistema de control de código fuente, probablemente debido a problemas de red o de contención.|  
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC_E_NONSPECIFICERROR|Error no específico; no se quitó el archivo.|  
|SCC_I_OPERATIONCANCELED|La operación se canceló antes de completarse.|  
  
## <a name="remarks"></a>Comentarios  
 Esta función quita los archivos del sistema de control de código fuente, pero no los elimina de la unidad de disco duro local del usuario.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)