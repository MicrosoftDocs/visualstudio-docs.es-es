---
title: IDebugPortRequest2::GetPortName | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 11097133a3f37058e71ed81a1dd73b71480f27e0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49185450"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene el nombre del puerto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```csharp  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrPortName`  
 [out] Devuelve el nombre del puerto.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) interfaz normalmente se pasa de un paquete de depuración (el cliente) a un proveedor de puerto (el servidor) para obtener una conexión a un puerto. El paquete de depuración y el proveedor del puerto son conscientes de las opciones posibles para el puerto. Si una cadena sencilla puede describir el puerto, el `IDebugPortRequest2::GetPortName` método tiene información suficiente para realizar la conexión. En caso contrario, se pueden proporcionar interfaces adicionales por el cliente, que puede obtenerse mediante el uso de servidor `IDebugPortRequest2::QueryInterface`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)

