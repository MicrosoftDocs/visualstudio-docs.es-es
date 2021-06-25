---
title: Enumerador de código de estado de directorio | Microsoft Docs
description: El enumerador SccDirStatus contiene valores constantes con nombre que especifican el estado de un directorio en el sistema de control de código fuente y SccDirQueryInfo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a504c6c080c34b4506cf4078b64465a3bd6c7d97
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904235"
---
# <a name="directory-status-code-enumerator"></a>Enumerador de código de estado de directorio
El `SccDirStatus` enumerador contiene valores constantes con nombre que especifican el estado de un directorio en el sistema de control de código fuente. [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)usa esta enumeración. Esto se introdujo en la versión 1.2 de la API de complemento de control de código fuente.

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
 SCC_DIRSTATUS_INVALID estado no se pudo obtener; no se basan en él.

 SCC_DIRSTATUS_NOTCONTROLLED Directory no está bajo control de código fuente.

 SCC_DIRSTATUS_CONTROLLED Directory está bajo control de código fuente.

 SCC_DIRSTATUS_EMPTYPROJ proyecto correspondiente a este directorio está vacío.

## <a name="see-also"></a>Consulta también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
