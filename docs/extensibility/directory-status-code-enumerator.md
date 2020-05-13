---
title: Enumerador de código de estado de directorio ( Directory Status Code Enumerator) Microsoft Docs
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
ms.openlocfilehash: 7b5ebf61f2baa6e4277e27cd3c4d18a51e64f835
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712154"
---
# <a name="directory-status-code-enumerator"></a>Enumerador de código de estado de directorio
El `SccDirStatus` enumerador contiene valores constantes con nombre que especifican el estado de un directorio en el sistema de control de código fuente. [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)utiliza esta enumeración. Esto se introdujo en la versión 1.2 de la API de complemento de Control de código fuente.

## <a name="syntax"></a>Sintaxis

```
enum SccDirStatus {
   SCC_DIRSTATUS_INVALID       = -1L,
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L
};
```

## <a name="members"></a>Miembros
 SCC_DIRSTATUS_INVALID no se pudo obtener el estatus; no confíe en él.

 SCC_DIRSTATUS_NOTCONTROLLED Directory no está bajo control de código fuente.

 directorio de SCC_DIRSTATUS_CONTROLLED está bajo control de código fuente.

 SCC_DIRSTATUS_EMPTYPROJ proyecto correspondiente a este directorio está vacío.

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
