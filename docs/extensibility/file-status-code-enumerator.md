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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94bd9ff93872139fc056c4c8bb7a59191616919e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342690"
---
# <a name="file-status-code-enumerator"></a>Enumerador de código de estado de archivo
El `SccStatus` enumerador contiene valores constantes con nombre que especifican el estado de un archivo en el sistema de control de código fuente. Esta enumeración se utiliza en el [SccQueryInfo](../extensibility/sccqueryinfo-function.md) y `POPLISTFUNC` función de devolución de llamada (consulte [POPLISTFUNC](../extensibility/poplistfunc.md) para obtener más información).

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
 No se pudo obtener el estado de SCC_STATUS_INVALID; No confíe en él.

 Archivo de SCC_STATUS_NOTCONTROLLED no está bajo control de código fuente.

 SCC_STATUS_CONTROLLED archivo está bajo control de código fuente.

 SCC_STATUS_CHECKEDOUT activada por el usuario actual en el disco local.

 SCC_STATUS_OUTOTHER archivo está desprotegido por otro usuario.

 Archivo SCC_STATUS_OUTEXCLUSIVE estaba desprotegido.

 SCC_STATUS_OUTMULTIPLE archivo está desprotegido por más de un usuario.

 SCC_STATUS_OUTOFDATE el archivo no es la más reciente.

 Se eliminó el archivo SCC_STATUS_DELETED desde el proyecto.

 El archivo SCC_STATUS_LOCKED está bloqueado; No hay versiones más permitidas.

 Archivo SCC_STATUS_MERGED se ha combinado pero todavía no se ha corregido y comprobado.

 Archivo SCC_STATUS_SHARED es compartido entre proyectos.

 Archivo SCC_STATUS_PINNED se comparte en una versión explícita.

 Archivo SCC_STATUS_MODIFIED ha sido modificado, interrumpido o infringido.

 SCC_STATUS_OUTBYUSER archivo está desprotegido por el usuario actual.

 Archivo SCC_STATUS_NOMERGE nunca se pueden mezclar con y no deben guardarse antes de una operación GET.

 SCC_STATUS_RESERVED_1 reservado para uso interno.

 SCC_STATUS_RESERVED_2 reservado para uso interno.

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)