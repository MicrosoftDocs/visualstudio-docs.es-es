---
description: Obtiene el nombre del atributo personalizado.
title: 'IDebugCustomAttribute:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7be47a763d4809d6e62b65660c39187d2d130065
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088073"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Obtiene el nombre del atributo personalizado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetName( 
   BSTR* bstrName
);
```

```csharp
int GetName(
   out string bstrName
);
```

## <a name="parameters"></a>Parámetros
`bstrName`\
enuncia Devuelve una cadena que contiene el nombre del atributo personalizado.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El denominado devuelto por este método corresponde al nombre de la clase utilizada para declarar el atributo. Esto puede no corresponder exactamente al nombre de la propia clase de atributo personalizado como C# permite quitar el sufijo "Attribute" de un nombre de atributo personalizado cuando se usa en una declaración.

## <a name="see-also"></a>Consulte también
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
