---
title: 'IDebugDefaultPort2:: QueryIsLocal | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2a4c4f5d8e9810f0828ac5ffb85173ef9ed77626
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896232"
---
# <a name="idebugdefaultport2queryislocal"></a>IDebugDefaultPort2::QueryIsLocal
Este método determina si este puerto está en el equipo local.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT QueryIsLocal(
   void
);
```

```csharp
int QueryIsLocal();
```

## <a name="return-value"></a>Valor devuelto
 Devuelve `S_OK` si este puerto es local (en el mismo equipo que el autor de la llamada) o `S_FALSE` si el puerto está en otro equipo.

## <a name="see-also"></a>Vea también
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
