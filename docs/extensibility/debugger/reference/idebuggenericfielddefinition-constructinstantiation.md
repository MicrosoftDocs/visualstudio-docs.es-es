---
title: IDebugGenericFieldDefinition::ConstructInstantiation | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d2a7c9b85c3025e3e23bbd316c84fce9f0d741fc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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
 [in] Matriz que contiene los argumentos de tipo. Los argumentos de tipo deben ser tipos cerrados (genéricos no son genéricas o instancias completas).  
  
 `ppConstructedField`  
 [out] Devuelve el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaz que representa el nuevo campo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 No se comprueban las restricciones.  
  
## <a name="see-also"></a>Vea también  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)