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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c6d5eb64cf4883c2e977b41e77fc2243aca2ee34
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968260"
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

## <a name="members"></a>Members
 No se pudo obtener el estado de SCC_DIRSTATUS_INVALID; no se base en él.

 SCC_DIRSTATUS_NOTCONTROLLED directorio no está bajo control de código fuente.

 SCC_DIRSTATUS_CONTROLLED directorio está bajo control de código fuente.

 SCC_DIRSTATUS_EMPTYPROJ proyecto correspondiente a este directorio está vacío.

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
