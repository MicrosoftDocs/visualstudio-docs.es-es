---
title: 'IDebugPortRequest2:: GetPortName | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: afed0bb700f41f7c39551f1a9bc7779f36b0ae57
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188364"
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
 enuncia Devuelve el nombre del puerto.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La interfaz [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) normalmente se pasa desde un paquete de depuración (el cliente) a un proveedor de puerto (el servidor) para obtener una conexión a un puerto. Tanto el paquete de depuración como el proveedor del puerto reconocen las posibles opciones para el puerto. Si una cadena simple puede describir el puerto, el `IDebugPortRequest2::GetPortName` método tiene información suficiente para establecer la conexión. De lo contrario, el cliente puede proporcionar otras interfaces, que puede obtener el servidor mediante `IDebugPortRequest2::QueryInterface` .  
  
## <a name="see-also"></a>Consulte también  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
