---
title: SccGetUserOption (función) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b906dc9585ed51640ca36f366fe6a1b0d3a03aa2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928209"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption (Función)
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
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Opción se recuperó correctamente.|  
|SCC_E_OPNOTSUPPORTED|No se admite la opción.|  
|SCC_E_NONSPECIFICERROR|Se ha producido un error no especificado.|  
  
## <a name="remarks"></a>Comentarios  
 Este comando admite las siguientes opciones:  
  
|Opción de usuario|Descripción|  
|-----------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Determina si el usuario desea desproteger versión local de archivos. `lpVal` se asigna `SCC_USEROPT_COLV_YES` (usuario desea desproteger los archivos locales) o `SCC_USEROPT_COLV_NO`.|  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Códigos de error](../extensibility/error-codes.md)