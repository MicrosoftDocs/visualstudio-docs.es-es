---
title: Función SccGetUserOption | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bd00a2b669b806b09a6ae221b2ba2e03f8d45ceb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200074"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función recupera una variedad de opciones específicas del usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pContext  
 de Puntero de contexto del complemento de control de código fuente.  
  
 nOption  
 de Opción para recuperar (vea la sección Comentarios para ver las posibles opciones).  
  
 lpVal  
 enuncia Valor asociado a la opción.  
  
## <a name="return-value"></a>Valor devuelto  
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:  
  
|Value|Descripción|  
|-----------|-----------------|  
|SCC_OK|La opción se recuperó correctamente.|  
|SCC_E_OPNOTSUPPORTED|No se admite la opción.|  
|SCC_E_NONSPECIFICERROR|Se ha producido un error no especificado.|  
  
## <a name="remarks"></a>Observaciones  
 Este comando admite las siguientes opciones:  
  
|Opción de usuario|Descripción|  
|-----------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Determina si el usuario desea desproteger la versión local de los archivos. `lpVal` se asigna `SCC_USEROPT_COLV_YES` (el usuario desea desproteger los archivos locales) o `SCC_USEROPT_COLV_NO` .|  
  
## <a name="see-also"></a>Consulte también  
 [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Códigos de error](../extensibility/error-codes.md)
