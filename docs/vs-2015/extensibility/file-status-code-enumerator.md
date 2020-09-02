---
title: Enumerador de código de estado de archivo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1b6e74caa9eedd42e25339d62f5837ccfe82d001
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204380"
---
# <a name="file-status-code-enumerator"></a>Enumerador de código de estado de archivo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 SCC_STATUS_INVALID  
 No se pudo obtener el estado. no se base en él.  
  
 SCC_STATUS_NOTCONTROLLED  
 El archivo no está bajo control de código fuente.  
  
 SCC_STATUS_CONTROLLED  
 El archivo está bajo control de código fuente.  
  
 SCC_STATUS_CHECKEDOUT  
 Desprotegido por el usuario actual en el disco local.  
  
 SCC_STATUS_OUTOTHER  
 El archivo está desprotegido por otro usuario.  
  
 SCC_STATUS_OUTEXCLUSIVE  
 El archivo está desprotegido en exclusiva.  
  
 SCC_STATUS_OUTMULTIPLE  
 El archivo está desprotegido por más de un usuario.  
  
 SCC_STATUS_OUTOFDATE  
 El archivo no es el más reciente.  
  
 SCC_STATUS_DELETED  
 El archivo se ha eliminado del proyecto.  
  
 SCC_STATUS_LOCKED  
 El archivo está bloqueado; no se permiten más versiones.  
  
 SCC_STATUS_MERGED  
 El archivo se ha combinado pero aún no se ha corregido o comprobado.  
  
 SCC_STATUS_SHARED  
 El archivo se comparte entre proyectos.  
  
 SCC_STATUS_PINNED  
 El archivo se comparte con una versión explícita.  
  
 SCC_STATUS_MODIFIED  
 El archivo se ha modificado, interrumpido o infringido.  
  
 SCC_STATUS_OUTBYUSER  
 El archivo está desprotegido por el usuario actual.  
  
 SCC_STATUS_NOMERGE  
 El archivo nunca se puede combinar con y no es necesario guardarlo antes de una obtención.  
  
 SCC_STATUS_RESERVED_1  
 Reservado para uso interno.  
  
 SCC_STATUS_RESERVED_2  
 Reservado para uso interno.  
  
## <a name="see-also"></a>Consulte también  
 [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)
