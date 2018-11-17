---
title: IDebugMethodField::EnumArguments | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b3ac8a689204cd9fb36c8d4b9c1fda4d6789fdcf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809433"
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
 [out] Devuelve un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa la lista de tipos de argumento. Devuelve un valor null si no hay ningún argumento.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK o devuelve S_FALSE si no hay ningún argumento. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cada elemento es un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objetos que representan los tipos de cada parámetro. Llame a la [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) método para recuperar información sobre el tipo de cada parámetro.  
  
 Si se necesita el nombre del parámetro junto con el tipo, a continuación, llame a la [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)

