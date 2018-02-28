---
title: IDebugMethodField::EnumLocals | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 451c2ccad7d817946bd3d2c2e83ed27279124f2b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Crea un enumerador para seleccionado variables locales del método.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT EnumLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pAddress`  
 [in] Un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objeto que representa la dirección de depuración que selecciona al contexto o ámbito desde el que se va a obtener las variables locales.  
  
 `ppLocals`  
 [out] Devuelve un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) el objeto que representa una lista de las variables locales; de lo contrario, devuelve un valor null si no hay ningún variables locales.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK o devuelva S_FALSE si no hay ningún variables locales. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Se enumeran solo las variables definidas dentro del bloque que contiene la dirección de depuración especificado. Si se necesitan todas las variables locales incluidas las variables locales generadas por el compilador, llame a la [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) método.  
  
 Un método puede contener varios contextos o bloques de ámbito. Por ejemplo, el siguiente método inventado contiene tres ámbitos, los dos bloques internos y el cuerpo del método.  
  
```csharp  
public void func(int index)  
{  
    // Method body scope  
    int a = 0;  
    if (index == 1)  
    {  
        // Inner scope 1  
        int temp1 = a;  
    }  
    else  
    {  
        // Inner scope 2  
        int temp2 = a;  
    }  
}  
```  
  
 El [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) objeto representa el `func` propio método. Llamar a la `EnumLocals` método con un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) establecido en el `Inner Scope 1` dirección devuelve una enumeración que contiene el `temp1` variable, por ejemplo.  
  
## <a name="see-also"></a>Vea también  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)