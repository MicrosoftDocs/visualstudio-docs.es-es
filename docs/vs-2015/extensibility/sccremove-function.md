---
title: Función SccRemove | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 62974f585fe164c7ccf7ea21a19d22939d806d73
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199969"
---
# <a name="sccremove-function"></a>SccRemove (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función elimina archivos del sistema de control de código fuente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 de Estructura de contexto del complemento de control de código fuente.  
  
 hWnd  
 de Identificador de la ventana del IDE que el complemento de control de código fuente puede utilizar como elemento primario para los cuadros de diálogo que proporciona.  
  
 N archivos  
 de Número de archivos especificados en la `lpFileNames` matriz.  
  
 lpFileNames  
 de Matriz de nombres de ruta de acceso local completa de los archivos que se van a quitar.  
  
 lpComment  
 de Comentario que se va a aplicar a cada archivo que se va a quitar.  
  
 Opciones  
 de Marcas de comando (sin usar).  
  
 pvOptions  
 de Opciones específicas del complemento de control de código fuente.  
  
## <a name="return-value"></a>Valor devuelto  
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:  
  
|Value|Descripción|  
|-----------|-----------------|  
|SCC_OK|Eliminación correcta.|  
|SCC_E_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|  
|SCC_E_OPNOTSUPPORTED|El sistema de control de código fuente no admite esta operación.|  
|SCC_E_ISCHECKEDOUT|No se puede quitar un archivo porque un usuario tiene desprotegido.|  
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención.|  
|SCC_E_NOTAUTHORIZED|El usuario no tiene permiso para realizar esta operación.|  
|SCC_E_NONSPECIFICERROR|Error no específico; no se quitó el archivo.|  
|SCC_I_OPERATIONCANCELED|La operación se canceló antes de completarse.|  
  
## <a name="remarks"></a>Comentarios  
 Esta función quita los archivos del sistema de control de código fuente, pero no Los elimina del disco duro local del usuario.  
  
## <a name="see-also"></a>Consulte también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
