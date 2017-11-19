---
title: "Función SccRename | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccRename
helpviewer_keywords: SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2936c2ea4425ad6eaccc2d23853f4174e1c9c2a2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="sccrename-function"></a>SccRename (función)
Esta función cambia el nombre de un archivo en el sistema de control de código fuente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccRename(  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName,  
   LPCSTR lpNewName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pvContext  
 [in] La estructura de contexto de complemento de control de código fuente.  
  
 hWnd  
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 lpFileName  
 [in] El nombre de archivo completo del archivo que se va a cambiar el nombre.  
  
 lpNewName  
 [in] El nombre completo de nuevo. Si la ruta del directorio es diferente, el archivo se movió de un subdirectorio a otro.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|La operación de cambio de nombre que se completó correctamente.|  
|SCC_E_PROJNOTOPEN|El proyecto no está abierto en el control de código fuente.|  
|SCC_E_FILENOTCONTROLLED|El archivo no está bajo control de código fuente.|  
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención.|  
|SCC_E_NOTAUTHORIZED|El usuario no está autorizado para completar esta operación.|  
|SCC_E_COULDNOTCREATEPROJECT|No se pudo crear el proyecto como parte del proceso de cambio de nombre.|  
|SCC_E_OPNOTPERFORMED|No se realizó la operación.|  
|SCC_E_NONSPECIFICERROR|Se produjo un error no especificado o general.|  
  
## <a name="remarks"></a>Comentarios  
 Esta función puede utilizarse para cambiar el nombre de un archivo o moverlo de una ubicación a otra en el sistema de control de código fuente. El complemento de control de código fuente no debería intentar tener acceso al archivo en disco. Es responsabilidad del IDE para cambiar el nombre del archivo local.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)