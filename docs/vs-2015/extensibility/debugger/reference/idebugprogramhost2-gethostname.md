---
title: IDebugProgramHost2::GetHostName | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb7ceae40282115dc455691789c3882a1620e829
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68165116"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene el título, el nombre descriptivo o el nombre de archivo del proceso de hospedaje de este programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 En una implementación típica de este método, el `dwType` parámetro se omite y se devuelve un nombre descriptivo de la máquina host. Otra posible implementación consiste en pasar el `dwType` parámetro a una llamada a la [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) método para obtener el nombre.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
