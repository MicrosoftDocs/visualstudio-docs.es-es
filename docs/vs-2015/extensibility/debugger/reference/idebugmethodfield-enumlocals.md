---
title: 'IDebugMethodField:: EnumLocals | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2306bbf0c44a883c584346c3dbb3dd70e9b39175
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162609"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea un enumerador para las variables locales seleccionadas del método.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 de Un objeto [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) que representa la dirección de depuración que selecciona el contexto o el ámbito desde el que se van a obtener las variables locales.  
  
 `ppLocals`  
 enuncia Devuelve un objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa una lista de variables locales; de lo contrario, devuelve un valor NULL si no hay variables locales.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, Devuelve S_OK o devuelve S_FALSE si no hay variables locales. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Solo se enumeran las variables definidas dentro del bloque que contiene la dirección de depuración especificada. Si se necesitan todas las variables locales, incluidas las variables locales generadas por el compilador, llame al método [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) .  
  
 Un método puede contener varios contextos de ámbito o bloques. Por ejemplo, el siguiente método inventado contiene tres ámbitos, los dos bloques internos y el propio cuerpo del método.  
  
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
  
 El objeto [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) representa el `func` propio método. La llamada al `EnumLocals` método con un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) establecido en la `Inner Scope 1` Dirección devuelve una enumeración que contiene la `temp1` variable, por ejemplo.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
