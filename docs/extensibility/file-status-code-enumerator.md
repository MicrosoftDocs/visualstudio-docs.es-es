---
title: Enumerador de código de estado de archivo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 184c8686ea184aea2cbd0a64873718cbe72f7615
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711453"
---
# <a name="file-status-code-enumerator"></a>Enumerador de código de estado de archivo
El `SccStatus` enumerador contiene valores constantes con nombre que especifican el estado de un archivo en el sistema de control de código fuente. Esta enumeración la usan [SccQueryInfo](../extensibility/sccqueryinfo-function.md) y la `POPLISTFUNC` función de devolución de llamada (vea [POPLISTFUNC](../extensibility/poplistfunc.md) para obtener más información).

## <a name="syntax"></a>Sintaxis

```
enum SccStatus {
   SCC_STATUS_INVALID          = -1L,
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,
   SCC_STATUS_CONTROLLED       = 0x0001L,
   SCC_STATUS_CHECKEDOUT       = 0x0002L,
   SCC_STATUS_OUTOTHER         = 0x0004L,
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,
   SCC_STATUS_OUTOFDATE        = 0x0020L,
   SCC_STATUS_DELETED          = 0x0040L,
   SCC_STATUS_LOCKED           = 0x0080L,
   SCC_STATUS_MERGED           = 0x0100L,
   SCC_STATUS_SHARED           = 0x0200L,
   SCC_STATUS_PINNED           = 0x0400L,
   SCC_STATUS_MODIFIED         = 0x0800L,
   SCC_STATUS_OUTBYUSER        = 0x1000L
   SCC_STATUS_NOMERGE          = 0x2000L
   SCC_STATUS_RESERVED_1       = 0x4000L
   SCC_STATUS_RESERVED_2       = 0x8000L
};
```

## <a name="members"></a>Miembros
 No se pudo obtener el estado de SCC_STATUS_INVALID; no se base en él.

 SCC_STATUS_NOTCONTROLLED archivo no está bajo control de código fuente.

 SCC_STATUS_CONTROLLED archivo está bajo control de código fuente.

 SCC_STATUS_CHECKEDOUT desprotegido por el usuario actual en el disco local.

 Otro usuario desprotegió SCC_STATUS_OUTOTHER archivo.

 SCC_STATUS_OUTEXCLUSIVE archivo está desprotegido en exclusiva.

 SCC_STATUS_OUTMULTIPLE archivo está desprotegido por más de un usuario.

 SCC_STATUS_OUTOFDATE el archivo no es el más reciente.

 SCC_STATUS_DELETED archivo se ha eliminado del proyecto.

 SCC_STATUS_LOCKED archivo está bloqueado; no se permiten más versiones.

 SCC_STATUS_MERGED archivo se ha combinado pero aún no se ha corregido o comprobado.

 SCC_STATUS_SHARED archivo se comparte entre proyectos.

 SCC_STATUS_PINNED archivo se comparte en una versión explícita.

 SCC_STATUS_MODIFIED archivo se ha modificado o interrumpido.

 SCC_STATUS_OUTBYUSER archivo está desprotegido por el usuario actual.

 SCC_STATUS_NOMERGE archivo nunca se puede combinar con y no es necesario guardarlo antes de un GET.

 SCC_STATUS_RESERVED_1 reservado para uso interno.

 SCC_STATUS_RESERVED_2 reservado para uso interno.

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
