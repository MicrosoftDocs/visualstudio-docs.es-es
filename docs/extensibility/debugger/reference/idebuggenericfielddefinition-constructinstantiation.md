---
title: IDebugGenericFieldDefinition::ConstructInstantiation | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: cc2c710e7fbd9a6fef3283f6dc5790707c65d30a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933058"
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