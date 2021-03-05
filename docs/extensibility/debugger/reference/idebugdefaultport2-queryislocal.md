---
description: Este método determina si este puerto está en el equipo local.
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
ms.openlocfilehash: f732de2526aa71698b4c01a636dab541050015a5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150645"
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

## <a name="see-also"></a>Consulte también
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
