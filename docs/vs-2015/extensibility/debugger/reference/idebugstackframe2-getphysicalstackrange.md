---
title: IDebugStackFrame2::GetPhysicalStackRange | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c48943ba68bf4090fd6d2b65b3ffba1f5018af2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579483"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugStackFrame2::GetPhysicalStackRange](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange).  
  
Obtiene una representación de dependiente de la máquina del intervalo de direcciones físicas asociado con un marco de pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetPhysicalStackRange (   
   UINT64* paddrMin,  
   UINT64* paddrMax  
);  
```  
  
```csharp  
int GetPhysicalStackRange (   
   out ulong paddrMin,  
   out ulong paddrMax  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `paddrMin`  
 [out] Devuelve el menor dirección física asociada con este marco de pila.  
  
 `paddrMax`  
 [out] Devuelve la dirección física más alta asociada con este marco de pila.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La información devuelta por este método se utiliza el Administrador de depuración de la sesión (SDM) para ordenar los marcos de pila.  
  
 Se supone que la pila de llamadas crece hacia abajo, es decir, que se han agregado nuevos marcos de pila en las direcciones de memoria cada vez más inferiores. Una arquitectura en tiempo de ejecución debe proporcionar los intervalos de pila física que coinciden con esta suposición.  
  
## <a name="see-also"></a>Vea también  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)

