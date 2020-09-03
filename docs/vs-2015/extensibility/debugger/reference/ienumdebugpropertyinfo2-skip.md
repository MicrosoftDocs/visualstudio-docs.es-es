---
title: 'IEnumDebugPropertyInfo2:: Skip | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2::Skip
helpviewer_keywords:
- IEnumDebugPropertyInfo2::Skip
ms.assetid: 0366c778-18eb-4065-a452-64b70c751a58
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b6cac15899adef12a4a06ab0b2dca3c051ecbd5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182394"
---
# <a name="ienumdebugpropertyinfo2skip"></a>IEnumDebugPropertyInfo2::Skip
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Omite el número de elementos especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] Número de elementos que se van a omitir.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si `celt` es mayor que el número de elementos restantes; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Observaciones  
 Si `celt` especifica un valor mayor que el número de elementos restantes, la enumeración se establece en el final y `S_FALSE` se devuelve.  
  
## <a name="see-also"></a>Consulte también  
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
