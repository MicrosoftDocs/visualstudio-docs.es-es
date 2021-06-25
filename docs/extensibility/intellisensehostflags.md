---
title: IntelliSenseHostFlags | Microsoft Docs
description: La enumeración IntelliSenseHostFlags especifica marcas de host de IntelliSense. En este artículo se describen los valores de enumeración.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 33345f86c69d0faeaa5863534e21eca5ecc176cc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902623"
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
|`IHF_NOSEPARATESUBJECT`|Sin texto del asunto. El búfer de contexto contiene IntelliSense-target (implica `!IHF_READONLYCONTEXT` ).|
|`IHF_SINGLELINESUBJECT`|El texto del asunto no es compatible con varias líneas.|
|`IHF_FORCECOMMITTOCONTEXT`|Igual a `CanCommitIntoReadOnlyBuffer`.|
|`IHF_OVERTYPE`|La edición (en el asunto o el contexto) debe realizarse en modo de sobretipo.|

## <a name="requirements"></a>Requisitos
 SingleFileeditor.idl

## <a name="see-also"></a>Consulte también
- <xref:Microsoft.VisualStudio.TextManager.Interop>
