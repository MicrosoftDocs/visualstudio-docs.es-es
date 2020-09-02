---
title: 'IDebugPortSupplier2:: CanAddPort | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e4ec078650446d3511ed9c5bdc8ee3ec0191487d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188350"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Comprueba que un proveedor de puerto puede agregar nuevos puertos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT CanAddPort(   
   void   
);  
```  
  
```csharp  
int CanAddPort();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si se puede Agregar el puerto, devuelve `S_OK` ; de lo contrario, devuelve `S_FALSE` para indicar que no se pueden agregar puertos a este proveedor de puertos.  
  
## <a name="remarks"></a>Observaciones  
 Llame a este método antes de llamar al método [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) , ya que el último método crea el puerto y lo agrega, lo que podría ser una operación que consume mucho tiempo.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
