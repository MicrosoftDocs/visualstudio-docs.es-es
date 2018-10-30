---
title: IDebugExtendedField::IsClosedType | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 418a25fb5b23bcedf53b0b1af8fe8ddae0bc48c9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863092"
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
Determina si el campo representa un tipo cerrado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT IsClosedType(  
   void  
);  
```  
  
```csharp  
int IsClosedType();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve si el campo es un tipo cerrado, `S_OK`; en caso contrario, devuelve `S_FALSE`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)