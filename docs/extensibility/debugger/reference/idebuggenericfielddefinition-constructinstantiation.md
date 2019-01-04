---
title: IDebugGenericFieldDefinition::ConstructInstantiation | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6f72e251f66c196ec36eb68f5a228536658ab89d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823952"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
Crea una instancia del campo dada una matriz de argumentos de tipo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT ConstructInstantiation(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   IDebugField** ppConstructedField  
);  
```  
  
```csharp  
int ConstructInstantiation(  
   uint            cArgs,  
   IDebugField[]   ppArgs,  
   out IDebugField ppConstructedField  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cArgs`  
 [in] Número de argumentos de la `ppArgs` matriz.  
  
 `ppArgs`  
 [in] Matriz que contiene los argumentos de tipo. Los argumentos de tipo deben ser tipos cerrados (genéricos no genérica o totalmente con instancias).  
  
 `ppConstructedField`  
 [out] Devuelve el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaz que representa el nuevo campo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 No se comprueban las restricciones.  
  
## <a name="see-also"></a>Vea también  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)