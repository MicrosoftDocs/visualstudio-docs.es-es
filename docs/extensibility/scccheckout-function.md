---
title: "Función SccCheckout | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccCheckout
helpviewer_keywords: SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: af8aac642ecd21f8f4709874e4e3e6ff0b3e58b5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="scccheckout-function"></a>SccCheckout (función)
Proporciona una lista de nombres de archivo completo, esta función desprotege ellos en la unidad local. El comentario se aplica a todos los archivos que se desprotegen. El argumento de comentario puede ser un `null` cadena.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccCheckout (  
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
 [in] La estructura de contexto de complemento de control de código fuente.  
  
 hWnd  
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 nFiles  
 [in] Número de archivos seleccionados estén desprotegidos.  
  
 lpFileNames  
 [in] Matriz de nombres de ruta de acceso local completa de archivos que se va a desproteger.  
  
 lpComment  
 [in] Comentario que se aplicará a cada uno de los archivos seleccionados que se está desprotegidos.  
  
 fOptions  
 [in] Indicadores de comandos (vea [marcadores de bits utilizado por determinados comandos](../extensibility/bitflags-used-by-specific-commands.md)).  
  
 pvOptions  
 [in] Opciones de específicas del complemento de control de origen.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Desprotección fue correcta.|  
|SCC_E_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|  
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC_E_NONSPECIFICERROR|Error no determinado. El archivo no se ha desprotegido.|  
|SCC_E_ALREADYCHECKEDOUT|El usuario ya tiene desprotegido el archivo.|  
|SCC_E_FILEISLOCKED|El archivo está bloqueado, se prohíben la creación de nuevas versiones.|  
|SCC_E_FILEOUTEXCLUSIVE|Otro usuario ha realizado una desprotección exclusiva en este archivo.|  
|SCC_I_OPERATIONCANCELED|Se canceló la operación antes de la finalización.|  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Marcadores de bits utilizados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)