---
title: 'IDebugObject:: IsEqual | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 85252cdaf9fb076ebd4f8000115bcea576531bb1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159120"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Compara un objeto con este objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT IsEqual(   
   IDebugObject* pObject,  
   BOOL*         pfIsEqual  
);  
```  
  
```csharp  
int IsEqual(  
   IDebugObject pObject,  
   out int      pfIsEqual  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pObject`  
 de Objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa el objeto con el que se va a comparar.  
  
 `pfIsEqual`  
 enuncia Devuelve un valor distinto de cero ( `TRUE` ) si los valores de los objetos son iguales; de lo contrario, devuelve cero ( `FALSE` ).  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Observaciones  
 Normalmente, este método puede comparar las direcciones de los valores representados por el `pObject` parámetro y este objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ; si las direcciones son iguales, los objetos se pueden considerar iguales.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
