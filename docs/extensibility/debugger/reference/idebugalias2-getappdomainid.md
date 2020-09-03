---
title: 'IDebugAlias2:: GetAppDomainId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aca8f2311b58fc7e73f9eb4f4c14f993c88b9a62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736417"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Recupera el identificador del dominio de aplicación.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetAppDomainId (
   ULONG32* pappDomainId
);
```

```csharp
int GetAppDomainId (
   out uint pappDomainId
);
```

## <a name="parameters"></a>Parámetros
`pappDomainId`\
enuncia Devuelve el identificador del dominio de aplicación.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El identificador del dominio de aplicación cambia cada vez que se reinicia la aplicación y se crea un nuevo dominio de aplicación.

## <a name="see-also"></a>Vea también
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)
