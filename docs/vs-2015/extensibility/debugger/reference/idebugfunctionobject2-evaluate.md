---
title: 'IDebugFunctionObject2:: Evaluate | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c25e62dbfc0778fb1bf07c9108c9111f3520d87f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180971"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Llama a la función y devuelve el valor resultante como un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Evaluate (  
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwEvalFlags,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```csharp  
int Evaluate (  
   IDebugObject     ppParams,  
   uint             dwParams,  
   uint             dwEvalFlags,  
   uint             dwTimeout,  
   out IDebugObject ppResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppParams`  
 de Matriz de objetos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa los parámetros de entrada. Cada uno de estos parámetros se creó utilizando uno de los métodos Create en esta interfaz.  
  
 `dwParams`  
 de Número de parámetros de la `ppParams` matriz.  
  
 `dwEvalFlags`  
 de Combinación de marcas de la enumeración [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) que especifica cómo se va a realizar la evaluación.  
  
 `dwTimeout`  
 de Especifica el tiempo máximo, en milisegundos, que se va a esperar antes de que se devuelva desde este método. Use **infinita** para esperar indefinidamente.  
  
 `ppResult`  
 enuncia Devuelve un **IDebugObject** que representa el valor de la función como un objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
