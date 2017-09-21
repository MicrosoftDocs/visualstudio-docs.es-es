---
title: "IDebugMethodField::EnumLocals | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::EnumLocals"
helpviewer_keywords: 
  - "IDebugMethodField::EnumLocals (método)"
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugMethodField::EnumLocals
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un enumerador para las variables locales seleccionado del método.  
  
## Sintaxis  
  
```cpp#  
HRESULT EnumLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```c#  
int EnumLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### Parámetros  
 `pAddress`  
 \[in\]  Un objeto de [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) que representa la dirección de depuración que selecciona el contexto o el ámbito del que obtener los valores locales.  
  
 `ppLocals`  
 \[out\]  devuelve un objeto de [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa una lista de los valores locales; de lo contrario, devuelve un valor NULL si no hay valores locales.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK o devuelve S\_FALSE si no hay valores locales.  De lo contrario, devuelve un código de error.  
  
## Comentarios  
 Sólo las variables definido dentro del bloque que contiene la dirección especificada de depuración se enumeran.  Si todos los valores locales incluidos algunos valores locales usa son necesarios, llame al método de [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) .  
  
 Un método puede contener contextos o los varios bloques de ámbito.  Por ejemplo, el método ideado siguiente contiene tres ámbitos, los dos bloques internos y el cuerpo del método propio.  
  
```c#  
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
  
 El objeto de [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) representa el propio método de `func` .  Llamando al método de `EnumLocals` con [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) establecido en la dirección de `Inner Scope 1` devuelve una enumeración que contiene la variable de `temp1` , por ejemplo.  
  
## Vea también  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)