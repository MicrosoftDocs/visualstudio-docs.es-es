---
title: IDebugProgramHost2::GetHostName | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 17cb56589f9f045b2f478626c47857d5c951494c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Obtiene el título, el nombre descriptivo o el nombre de archivo del proceso de hospedaje de este programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```csharp  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwType`  
 [in] Un valor de la [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) enumeración.  
  
 `pbstrHostName`  
 [out] Devuelve el nombre del proceso de hospedaje solicitado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 En una implementación típica de este método, el `dwType` parámetro se omite y se devuelve un nombre descriptivo de la máquina host. Otra posible implementación consiste en pasar la `dwType` parámetro a una llamada a la [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) método para obtener el nombre.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)