---
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
ms.openlocfilehash: 6719968d2e828340b16f84f3195f722803d8d9d8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928736"
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

## <a name="remarks"></a>Notas
 Al menos uno de los parámetros debe devolver un valor distinto de NULL.

## <a name="see-also"></a>Vea también
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
