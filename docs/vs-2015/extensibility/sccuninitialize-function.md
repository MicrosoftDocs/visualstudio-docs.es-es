---
title: SccUninitialize (función) | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bcb0b3a6718cc90db6f7176c823ccccbbfc05f9a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68190849"
---
# <a name="sccuninitialize-function"></a>SccUninitialize (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función limpia asignaciones ni las conexiones abiertas que se creó mediante una llamada anterior a la [SccInitialize](../extensibility/sccinitialize-function.md) como preparación para cerrar el complemento de control de código fuente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pvContext  
 [in] El puntero a la estructura de contexto de complemento de control de origen que creó en el [SccInitialize](../extensibility/sccinitialize-function.md).  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:  
  
|Valor|DESCRIPCIÓN|  
|-----------|-----------------|  
|SCC_OK|La limpieza que se completó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 El complemento de control de código fuente es responsable de preparación para apagarse y para liberar memoria que ha asignado el complemento para la estructura de contexto. La función se llama una vez para cada instancia determinada de un complemento. Una llamada a la [SccInitialize](../extensibility/sccinitialize-function.md) precede a esta llamada. No hay proyectos todavía pueden estar abiertos en el momento de la llamada a `SccUninitialize`.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
