---
description: Obtiene la información de lenguaje para este contexto de código.
title: 'IDebugCodeContext2:: GetLanguageInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dccf0c34b6483ad85cc7bfd9cff7078cc20524f3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164128"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
Obtiene la información de lenguaje para este contexto de código.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetLanguageInfo( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo( 
   ref string pbstrLanguage,
   ref Guid pguidLanguage
);
```

## <a name="parameters"></a>Parámetros
`pbstrLanguage`\
[in, out] Devuelve una cadena que contiene el nombre del lenguaje, como "C++".

`pguidLanguage`\
[in, out] Devuelve el GUID del lenguaje del contexto de código, por ejemplo, `guidCPPLang` .

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Al menos uno de los parámetros debe devolver un valor distinto de NULL.

## <a name="see-also"></a>Consulte también
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
