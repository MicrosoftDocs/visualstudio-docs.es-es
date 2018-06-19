---
title: IDebugMethodField::EnumParameters | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 112b91c2155c28b37b2222a99a45893fcb56e98c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122202"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
Crea un enumerador para los parámetros del método.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT EnumParameters(   
   IEnumDebugFields** ppParams  
);  
```  
  
```csharp  
int EnumParameters(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppParams`  
 [out] Devuelve un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) el objeto que representa la lista de parámetros al método; en caso contrario, devuelve un valor null si no hay ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK o devuelva S_FALSE si no hay ningún parámetro. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cada elemento es un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto que representa los diferentes tipos de parámetros. Llame a la [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) método en cada objeto para determinar exactamente qué tipo de parámetro representa el objeto.  
  
 Un parámetro incluye su nombre de variable y su tipo. El primer parámetro a un método de clase normalmente es el puntero "this".  
  
 Si solo los tipos de los parámetros es necesario, llame a la [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)