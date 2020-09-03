---
title: 'IDebugMethodField:: EnumArguments | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5744e25f76676e70e25777596fb0d8eb3a580511
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205231"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea un enumerador para el tipo de cada argumento necesario para llamar al método.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT EnumArguments(   
   IEnumDebugFields** ppParams  
);  
```  
  
```csharp  
int EnumArguments(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppParams`  
 enuncia Devuelve un objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa la lista de tipos de argumento. Devuelve un valor NULL si no hay ningún argumento.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, Devuelve S_OK o devuelve S_FALSE si no hay ningún argumento. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Observaciones  
 Cada elemento es un objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa los tipos de cada parámetro. Llame al método [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) para recuperar información sobre el tipo de cada parámetro.  
  
 Si el nombre del parámetro es necesario junto con el tipo, llame al método [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) .  
  
## <a name="see-also"></a>Consulte también  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)
