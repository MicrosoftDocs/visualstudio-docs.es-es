---
title: Enumerador de código de estado | Microsoft Docs
description: El enumerador SccStatus contiene valores constantes que especifican el estado de un archivo en el sistema de control de código fuente y los usan SccQueryInfo y POPLISTFUNC.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 95de8a29efcd56880cdaf452c9f21b90bba1c5c9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900972"
---
# <a name="file-status-code-enumerator"></a>Enumerador de código de estado de archivo
El `SccStatus` enumerador contiene valores constantes con nombre que especifican el estado de un archivo en el sistema de control de código fuente. [SccQueryInfo](../extensibility/sccqueryinfo-function.md) y la función de devolución de llamada usan esta enumeración `POPLISTFUNC` [(vea POPLISTFUNC para](../extensibility/poplistfunc.md) obtener más información).

## <a name="syntax"></a>Sintaxis

```
enum SccStatus {
   SCC_STATUS_INVALID          = -1L,
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,
   SCC_STATUS_CONTROLLED       = 0x0001L,
   SCC_STATUS_CHECKEDOUT       = 0x0002L,
   SCC_STATUS_OUTOTHER         = 0x0004L,
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,
   SCC_STATUS_OUTOFDATE        = 0x0020L,
   SCC_STATUS_DELETED          = 0x0040L,
   SCC_STATUS_LOCKED           = 0x0080L,
   SCC_STATUS_MERGED           = 0x0100L,
   SCC_STATUS_SHARED           = 0x0200L,
   SCC_STATUS_PINNED           = 0x0400L,
   SCC_STATUS_MODIFIED         = 0x0800L,
   SCC_STATUS_OUTBYUSER        = 0x1000L
   SCC_STATUS_NOMERGE          = 0x2000L
   SCC_STATUS_RESERVED_1       = 0x4000L
   SCC_STATUS_RESERVED_2       = 0x8000L
};
```

## <a name="members"></a>Miembros
 SCC_STATUS_INVALID estado no se pudo obtener; no se basan en él.

 SCC_STATUS_NOTCONTROLLED archivo no está bajo control de código fuente.

 SCC_STATUS_CONTROLLED archivo está bajo control de código fuente.

 SCC_STATUS_CHECKEDOUT ha comprobado el usuario actual en el disco local.

 SCC_STATUS_OUTOTHER otro usuario desprotegía el archivo.

 SCC_STATUS_OUTEXCLUSIVE archivo está desprotegido exclusivamente.

 SCC_STATUS_OUTMULTIPLE más de un usuario desprotegía el archivo.

 SCC_STATUS_OUTOFDATE El archivo no es el más reciente.

 SCC_STATUS_DELETED archivo se ha eliminado del proyecto.

 SCC_STATUS_LOCKED archivo está bloqueado; no se permiten más versiones.

 SCC_STATUS_MERGED archivo se ha combinado, pero aún no se ha corregido ni comprobado.

 SCC_STATUS_SHARED archivo se comparte entre proyectos.

 SCC_STATUS_PINNED file se comparte con una versión explícita.

 SCC_STATUS_MODIFIED archivo se ha modificado, roto o infringido.

 SCC_STATUS_OUTBYUSER archivo está desprotegida por el usuario actual.

 SCC_STATUS_NOMERGE archivo no se puede combinar nunca con y no es necesario guardar antes de get.

 SCC_STATUS_RESERVED_1 reservado para uso interno.

 SCC_STATUS_RESERVED_2 reservado para uso interno.

## <a name="see-also"></a>Consulta también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
