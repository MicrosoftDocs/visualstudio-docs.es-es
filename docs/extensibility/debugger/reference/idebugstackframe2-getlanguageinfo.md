---
description: Obtiene el lenguaje asociado a este marco de pila.
title: 'IDebugStackFrame2:: GetLanguageInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetLanguageInfo
helpviewer_keywords:
- IDebugStackFrame2::GetLanguageInfo
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38d9cfcab6748aad2166bfddfb48e9a0c0dc90c0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159827"
---
# <a name="idebugstackframe2getlanguageinfo"></a>IDebugStackFrame2::GetLanguageInfo

Obtiene el lenguaje asociado a este marco de pila.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetLanguageInfo ( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo ( 
   ref string pbstrLanguage,
   ref Guid   pguidLanguage
);
```

## <a name="parameters"></a>Parámetros

`pbstrLanguage`\
enuncia Devuelve el nombre del lenguaje que implementa el método asociado a este marco de pila.

`pguidLanguage`\
enuncia Devuelve el `GUID` del idioma. Para los [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] lenguajes, por ejemplo, se puede devolver lo siguiente:

- `guidVBScriptLang`\

- `guidJScriptLang`\

- `guidCPPLang`\

- `guidVBLang`\

- `guidSQLLang`\

- `guidScriptLang`\

## <a name="return-value"></a>Valor devuelto

 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también

- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
