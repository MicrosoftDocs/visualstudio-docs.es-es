---
title: 'IEnumDebugCustomAttributes:: Next | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Next
helpviewer_keywords:
- IEnumDebugCustomAttributes::Next
ms.assetid: e36f856b-2619-42d1-b73e-4f2390fc22bd
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f6ce0a8199bfb279c8f8d628de0b174d7f03369
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62551408"
---
# <a name="ienumdebugcustomattributesnext"></a>IEnumDebugCustomAttributes::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera un número especificado de atributos personalizados en una secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Next (   
   ULONG      celt,  
   CODE_PATH* rgelt,  
   ULONG*     pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint                        celt,   
   out IDebugCustomAttribute[] rgelt,   
   ref uint                    pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] Número de elementos que se van a recuperar. También especifica el tamaño máximo de la `rgelt` matriz.  
  
 `rgelt`  
 enuncia Matriz de objetos [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) que se va a rellenar.  
  
 `pceltFetched`  
 enuncia Devuelve el número de elementos realmente devueltos en `rgelt` .  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si se puede devolver menos que el número solicitado de elementos; de lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Consulte también  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)   
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
