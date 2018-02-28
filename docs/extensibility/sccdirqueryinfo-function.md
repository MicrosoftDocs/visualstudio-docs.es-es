---
title: "Función SccDirQueryInfo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c7a930c0fcdffbc76bba431012d76dd6d13686d0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo (función)
Esta función examina una lista de directorios completos para su estado actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pContext  
 [in] La estructura de contexto de complemento de control de código fuente.  
  
 nDirs  
 [in] El número de directorios seleccionado para ser consultadas.  
  
 lpDirNames  
 [in] Una matriz de rutas de acceso completas de los directorios que se va a consultar.  
  
 lpStatus  
 [entrada, salida] Una estructura de matriz para el complemento para devolver las marcas de estado de control de código fuente (vea [código de estado de directorio](../extensibility/directory-status-code-enumerator.md) para obtener más información).  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|La consulta era correcta.|  
|SCC_E_OPNOTSUPPORTED|El sistema de control de código fuente no admite esta operación.|  
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Error no determinado.|  
  
## <a name="remarks"></a>Comentarios  
 La función rellena la matriz de devolución con una máscara de bits de bits de la `SCC_DIRSTATUS` familia (consulte [código de estado de directorio](../extensibility/directory-status-code-enumerator.md)), una entrada para cada directorio dado. La matriz de estados está asignada por el llamador.  
  
 El IDE usa esta función antes de que se cambia el nombre de un directorio para comprobar si el directorio está bajo control de código fuente mediante una consulta si tiene un proyecto correspondiente. Si el directorio no está bajo control de código fuente, el IDE puede proporcionar la advertencia adecuada para el usuario.  
  
> [!NOTE]
>  Si elige no implementar uno o varios de los valores de estado de un complemento de control de código fuente, bits no implementadas se deben establecer en cero.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Código de estado de directorio](../extensibility/directory-status-code-enumerator.md)