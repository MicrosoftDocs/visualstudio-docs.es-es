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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d0e66f70b91985882df5691d05175995b4f6ca8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328078"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Especifica las marcas de host de IntelliSense.

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
|`IHF_READONLYCONTEXT`|Búfer de contexto es de solo lectura.|
|`IHF_NOSEPARATESUBJECT`|No hay texto de asunto. Búfer de contexto contiene el destino de IntelliSense (implica `!IHF_READONLYCONTEXT`).|
|`IHF_SINGLELINESUBJECT`|Texto del asunto no es capaz varias líneas.|
|`IHF_FORCECOMMITTOCONTEXT`|Igual a `CanCommitIntoReadOnlyBuffer`.|
|`IHF_OVERTYPE`|Edición (en el asunto o el contexto) debe realizarse en modo de reemplazo.|

## <a name="requirements"></a>Requisitos
 SingleFileeditor.idl

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.TextManager.Interop>