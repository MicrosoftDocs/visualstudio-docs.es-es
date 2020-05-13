---
title: IntelliSenseHostFlags ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0df05e7363db01bd4f16fee5d75141dc93df1c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710268"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Especifica marcas de host de IntelliSense.

## <a name="syntax"></a>Sintaxis

```cpp
enum IntellisenseHostFlags
{
    IHF_READONLYCONTEXT      = 0x00000001
    IHF_NOSEPARATESUBJECT    = 0x00000002
    IHF_SINGLELINESUBJECT    = 0x00000004
    IHF_FORCECOMMITTOCONTEXT = 0x00000008
    IHF_OVERTYPE             = 0x00000010
};
```

### <a name="parameters"></a>Parámetros

|Miembros|Descripción|
|-------------|-----------------|
|`IHF_READONLYCONTEXT`|El búfer de contexto es de solo lectura.|
|`IHF_NOSEPARATESUBJECT`|No hay texto de asunto. El búfer de contexto contiene `!IHF_READONLYCONTEXT`IntelliSense-target (implica ).|
|`IHF_SINGLELINESUBJECT`|El texto del asunto no es compatible con varias líneas.|
|`IHF_FORCECOMMITTOCONTEXT`|Igual a `CanCommitIntoReadOnlyBuffer`.|
|`IHF_OVERTYPE`|La edición (en el asunto o el contexto) debe realizarse en modo de sobrescribir.|

## <a name="requirements"></a>Requisitos
 SingleFileeditor.idl

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.TextManager.Interop>
