---
title: IDebugDisassemblyStream2::GetSize | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDisassemblyStream2::GetSize
helpviewer_keywords: IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4ef3b4ed1f39b687812fa13d3a667b5e8fb91587
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdisassemblystream2getsize"></a>IDebugDisassemblyStream2::GetSize
Obtiene el tamaño de las instrucciones de esta secuencia de desensamblado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetSize(   
   UINT64* pnSize  
);  
```  
  
```csharp  
int GetSize(   
   out ulong pnSize  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pnSize`  
 [out] Devuelve el tamaño, en las instrucciones.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El valor devuelto de este método puede utilizarse para asignar una matriz de [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estructuras que, a continuación, se pasa a la [lectura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Lectura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)