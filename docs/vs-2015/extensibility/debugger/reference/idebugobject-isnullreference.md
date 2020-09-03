---
title: 'IDebugObject:: IsNullReference | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd116b236eb57e2fab638cfaa8412167a6d1180f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188888"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Comprueba si este objeto es una referencia nula.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT IsNullReference(   
   BOOL* pfIsNull  
);  
```  
  
```csharp  
int IsNullReference(  
   out int pfIsNull  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pfIsNull`  
 enuncia Devuelve un valor distinto de cero ( `TRUE` ) si este objeto es una referencia nula; de lo contrario, devuelve cero ( `FALSE` ).  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Observaciones  
 Una referencia nula significa un objeto vacío o un objeto que no se ha asignado a.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
