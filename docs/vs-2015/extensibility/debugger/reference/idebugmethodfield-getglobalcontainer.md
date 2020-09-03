---
title: 'IDebugMethodField:: GetGlobalContainer | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 63912b75435de503dec677b715d1914b419ba07a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162566"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene el contenedor global del método.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetGlobalContainer(  
   IDebugClassField** ppClass  
);  
```  
  
```csharp  
int GetGlobalContainer(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppClass`  
 enuncia Devuelve un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) que representa el módulo en el que se define este método.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Observaciones  
 El objeto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) devuelto representa todo el módulo y es un objeto artificial, es decir, el propio módulo no tiene una clase real, pero se puede representar mediante un `IDebugClassField` objeto, lo que permite enumerar y detectar los distintos elementos del módulo.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
