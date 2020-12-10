---
title: Enumerador de código de estado de directorio | Microsoft Docs
description: El enumerador SccDirStatus contiene valores constantes con nombre que especifican el estado de un directorio en el sistema de control de código fuente y se usa en SccDirQueryInfo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af72b9e14695cb954084abebc3a3c336c90af73d
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996128"
---
# <a name="directory-status-code-enumerator"></a>Enumerador de código de estado de directorio
El `SccDirStatus` enumerador contiene valores constantes con nombre que especifican el estado de un directorio en el sistema de control de código fuente. Esta enumeración la usa [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Esto se presentó en la versión 1,2 de la API del complemento de control de código fuente.

## <a name="syntax"></a>Sintaxis

```
enum SccDirStatus {
   SCC_DIRSTATUS_INVALID       = -1L,
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L
};
```

## <a name="members"></a>Miembros
 No se pudo obtener el estado de SCC_DIRSTATUS_INVALID; no se base en él.

 SCC_DIRSTATUS_NOTCONTROLLED directorio no está bajo control de código fuente.

 SCC_DIRSTATUS_CONTROLLED directorio está bajo control de código fuente.

 SCC_DIRSTATUS_EMPTYPROJ proyecto correspondiente a este directorio está vacío.

## <a name="see-also"></a>Consulte también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
