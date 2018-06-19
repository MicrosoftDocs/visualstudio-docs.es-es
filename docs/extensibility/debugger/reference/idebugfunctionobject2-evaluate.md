---
title: IDebugFunctionObject2::Evaluate | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8196eb45b2fe7eccbff5c23a7ffc58fd3eb59282
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112706"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
Llama a la función y devuelve el valor resultante como un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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
 [in] Una matriz de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objetos que representan los parámetros de entrada. Cada uno de estos parámetros se creó mediante uno de los métodos de creación de esta interfaz.  
  
 `dwParams`  
 [in] El número de parámetros en el `ppParams` matriz.  
  
 `dwEvalFlags`  
 [in] Una combinación de indicadores de la [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) enumeración que especifican cómo se realiza la evaluación.  
  
 `dwTimeout`  
 [in] Especifica el tiempo máximo, en milisegundos, que se esperará antes de volver de este método. Use **infinito** para esperar indefinidamente.  
  
 `ppResult`  
 [out] Devuelve un **IDebugObject** que representa el valor de la función como un objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)