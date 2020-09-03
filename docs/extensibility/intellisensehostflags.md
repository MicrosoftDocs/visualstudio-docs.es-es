---
title: IntelliSenseHostFlags | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
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
|`IHF_NOSEPARATESUBJECT`|Sin texto de asunto. El búfer de contexto contiene IntelliSense-destino (implica `!IHF_READONLYCONTEXT` ).|
|`IHF_SINGLELINESUBJECT`|El texto del asunto no es compatible con varias líneas.|
|`IHF_FORCECOMMITTOCONTEXT`|Igual a `CanCommitIntoReadOnlyBuffer`.|
|`IHF_OVERTYPE`|La edición (en asunto o contexto) debe realizarse en modo de sobretipo.|

## <a name="requirements"></a>Requisitos
 SingleFileeditor. idl

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.TextManager.Interop>
