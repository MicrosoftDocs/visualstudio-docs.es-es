---
title: Función SccUncheckout | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c363da795e588963c234af05a856f3352a7b2815
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137345"
---
# <a name="sccuncheckout-function"></a>SccUncheckout (función)
Esta función deshace una operación de desprotección anterior, restaurar, por tanto, el contenido del archivo seleccionado o los archivos al estado anterior a la desprotección. Se pierden todos los cambios realizados en el archivo desde la desprotección.  
  
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
 [in] La estructura de contexto de complemento de control de código fuente.  
  
 hWnd  
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 nFiles  
 [in] Número de archivos especificado en el `lpFileNames` matriz.  
  
 lpFileNames  
 [in] Matriz de nombres de ruta de acceso local completa de archivos para el que desea deshacer una desprotección.  
  
 fOptions  
 [in] Marcas de comando (no utilizados).  
  
 pvOptions  
 [in] Opciones de específicas del complemento de control de origen.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Deshacer desprotección fue correcta.|  
|SCC_E_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|  
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC_E_NONSPECIFICERROR|Error no determinado. Deshacer desprotección no se realizó correctamente.|  
|SCC_E_NOTCHECKEDOUT|El usuario no tiene el archivo desprotegido.|  
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC_E_PROJNOTOPEN|No se ha abierto el proyecto de control de código fuente.|  
|SCC_I_OPERATIONCANCELED|Se canceló la operación antes de la finalización.|  
  
## <a name="remarks"></a>Comentarios  
 Después de realizar esta operación, el `SCC_STATUS_CHECKEDOUT` y `SCC_STATUS_MODIFIED` marcas ambos se desactivarán para los archivos en el que se realizó la desprotección.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)