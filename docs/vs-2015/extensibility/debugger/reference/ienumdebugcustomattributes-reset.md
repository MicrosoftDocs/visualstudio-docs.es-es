---
title: 'IEnumDebugCustomAttributes:: RESET | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Reset
helpviewer_keywords:
- IEnumDebugCustomAttributes::Reset
ms.assetid: e0db6518-5a71-4adb-a407-4d2ac7a3e369
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ff86808bfd33cf7112091b028140f538932dee28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62551356"
---
# <a name="ienumdebugcustomattributesreset"></a>IEnumDebugCustomAttributes::Reset
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Restablece la secuencia de enumeración al principio.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Reset(void);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Después de llamar a este método, la siguiente llamada al método [siguiente](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) devuelve el primer elemento de la enumeración.  
  
## <a name="see-also"></a>Consulte también  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)   
 [Siguiente](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)
