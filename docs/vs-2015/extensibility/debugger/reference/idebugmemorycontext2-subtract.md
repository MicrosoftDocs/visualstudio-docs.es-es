---
title: 'IDebugMemoryContext2:: restar | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2efe4e15c5489ef07741a0d267b9c1b870d07aa8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146367"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Resta el valor especificado del contexto actual y devuelve un nuevo contexto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Subtract(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int Subtract(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwCount`  
 de Número de bytes de memoria que se van a reducir.  
  
 `ppMemCxt`  
 enuncia Devuelve un nuevo objeto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) .  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Un contexto de memoria es una dirección, por lo que restar un valor de una dirección genera una nueva dirección que requiere una nueva interfaz de contexto.  
  
 Este método siempre debe generar un nuevo contexto, incluso si la dirección resultante está fuera del espacio de memoria asociado a este contexto. La única excepción es si no se puede asignar memoria para el nuevo contexto o si `ppMemCxt` es un valor null (que es un error).  
  
## <a name="see-also"></a>Consulte también  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
