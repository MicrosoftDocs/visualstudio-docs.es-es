---
description: Determina si se ha definido un atributo personalizado específico.
title: 'IDebugMethodField:: IsCustomAttributeDefined | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7cd9e1ae31e893639b41537bb5b09323cc70ff9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081898"
---
# <a name="idebugmethodfieldiscustomattributedefined"></a>IDebugMethodField::IsCustomAttributeDefined
Determina si se ha definido un atributo personalizado específico.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT IsCustomAttributeDefined( 
   LPCOLESTR pszCustomAttributeName
);
```

```csharp
int IsCustomAttributeDefined(
   [In] string pszCustomAttributeName
);
```

## <a name="parameters"></a>Parámetros
`pszCustomAttributeName`\
de Cadena que contiene el nombre del atributo personalizado que se va a buscar.

## <a name="return-value"></a>Valor devuelto
 Devuelve S_OK si el atributo personalizado se define en este método; de lo contrario, devuelve S_FALSE.

## <a name="see-also"></a>Consulte también
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
