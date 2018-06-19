---
title: IDebugProgram2::EnumCodePaths | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56cc9580ec2e434066d1c0a3ce674a4111e433af
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122189"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Recupera una lista de las rutas de acceso de código para una posición determinada en un archivo de código fuente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT EnumCodePaths(   
   LPCOLESTR            pszHint,  
   IDebugCodeContext2*  pStart,  
   IDebugStackFrame2*   pFrame,  
   BOOL                 fSource,  
   IEnumCodePaths2**    ppEnum,  
   IDebugCodeContext2** ppSafety  
);  
```  
  
```csharp  
int EnumCodePaths(   
   string                 pszHint,  
   IDebugCodeContext2     pStart,  
   IDebugStackFrame2      pFrame,  
   Int                    fSource,  
   out IEnumCodePaths2    ppEnum,  
   out IDebugCodeContext2 ppSafety  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszHint`  
 [in] La palabra situada bajo el cursor en el **origen** o **desensamblado** vista en el IDE.  
  
 `pStart`  
 [in] Un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que representa el contexto actual del código.  
  
 `pFrame`  
 [in] Un [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) objeto que representa el marco de pila asociada con el punto de interrupción actual.  
  
 `fSource`  
 [in] Es distinto de cero (`TRUE`) si está en el **origen** vista, o cero (`FALSE`) si está en el **desensamblado** vista.  
  
 `ppEnum`  
 [out] Devuelve un [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) objeto que contiene una lista de las rutas de acceso del código.  
  
 `ppSafety`  
 [out] Devuelve un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que representa un contexto de código adicional que se establecerá como un punto de interrupción en caso de ruta de acceso de código de la elegida se ha omitido. Esto puede ocurrir en el caso de una expresión booleana cortocircuita, por ejemplo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Una ruta de acceso de código describe el nombre de un método o función que se llama para llegar al punto actual en la ejecución del programa. Una lista de las rutas de código representa la pila de llamadas.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)