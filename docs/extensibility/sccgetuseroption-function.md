---
title: "Función SccGetUserOption | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetUserOption
helpviewer_keywords: SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5c23e1fd5614963d8f52edc019e99287187fd9a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption (función)
Esta función recupera una variedad de opciones específicas del usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pContext  
 [in] El puntero de contexto de complemento de control de código fuente.  
  
 nOption  
 [in] Opción para recuperar (vea la sección Comentarios para las opciones posibles).  
  
 lpVal  
 [out] Valor asociado con la opción.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Opción se recuperó correctamente.|  
|SCC_E_OPNOTSUPPORTED|No se admite la opción.|  
|SCC_E_NONSPECIFICERROR|Se ha producido un error no especificado.|  
  
## <a name="remarks"></a>Comentarios  
 Este comando admite las siguientes opciones:  
  
|Opción de usuario|Descripción|  
|-----------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Determina si el usuario desea desproteger la versión local de archivos. `lpVal`se asigna `SCC_USEROPT_COLV_YES` (el usuario desea desproteger los archivos locales) o `SCC_USEROPT_COLV_NO`.|  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Códigos de error](../extensibility/error-codes.md)