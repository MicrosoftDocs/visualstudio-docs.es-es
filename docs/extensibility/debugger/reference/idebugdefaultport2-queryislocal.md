---
title: IDebugDefaultPort2::QueryIsLocal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a5becc75e76a0e219664ef07c148620fb2bc1e37
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53900404"
---
# <a name="idebugdefaultport2queryislocal"></a>IDebugDefaultPort2::QueryIsLocal
Este método determina si este puerto está en el equipo local.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT QueryIsLocal(  
   void  
);  
```  
  
```csharp  
int QueryIsLocal();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` si este puerto es local (en el mismo equipo que el llamador) o `S_FALSE` si el puerto está en otro equipo.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)