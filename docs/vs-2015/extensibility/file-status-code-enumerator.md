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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204380"
---
# <a name="file-status-code-enumerator"></a>Enumerador de código de estado de archivo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 SCC_STATUS_INVALID  
 No se pudo obtener el estado; No confíe en él.  
  
 SCC_STATUS_NOTCONTROLLED  
 Archivo no está bajo control de código fuente.  
  
 SCC_STATUS_CONTROLLED  
 Archivo está bajo control de código fuente.  
  
 SCC_STATUS_CHECKEDOUT  
 Desprotegido por el usuario actual en el disco local.  
  
 SCC_STATUS_OUTOTHER  
 Archivo está desprotegido por otro usuario.  
  
 SCC_STATUS_OUTEXCLUSIVE  
 Archivo está desprotegido en exclusiva.  
  
 SCC_STATUS_OUTMULTIPLE  
 Archivo está desprotegido por más de un usuario.  
  
 SCC_STATUS_OUTOFDATE  
 El archivo no es la más reciente.  
  
 SCC_STATUS_DELETED  
 Se eliminó el archivo del proyecto.  
  
 SCC_STATUS_LOCKED  
 El archivo está bloqueado; No hay versiones más permitidas.  
  
 SCC_STATUS_MERGED  
 Archivo se ha combinado pero todavía no se ha corregido y comprobado.  
  
 SCC_STATUS_SHARED  
 Archivo se comparte entre proyectos.  
  
 SCC_STATUS_PINNED  
 Archivo se comparte en una versión explícita.  
  
 SCC_STATUS_MODIFIED  
 Archivo ha sido modificado, interrumpido o infringido.  
  
 SCC_STATUS_OUTBYUSER  
 Archivo está desprotegido por el usuario actual.  
  
 SCC_STATUS_NOMERGE  
 Archivo nunca se puede mezclar con y no debe guardarse antes de una operación GET.  
  
 SCC_STATUS_RESERVED_1  
 Reservado para uso interno.  
  
 SCC_STATUS_RESERVED_2  
 Reservado para uso interno.  
  
## <a name="see-also"></a>Vea también  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)
