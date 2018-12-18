---
title: Enumerador de código de estado de archivo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 884c7ab1b5d4fe1461fd1ae00fbc670f0bc7b6f2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921020"
---
# <a name="file-status-code-enumerator"></a>Enumerador de código de estado de archivo
El `SccStatus` enumerador contiene valores constantes con nombre que especifican el estado de un archivo en el sistema de control de código fuente. Esta enumeración se utiliza en el [SccQueryInfo](../extensibility/sccqueryinfo-function.md) y `POPLISTFUNC` función de devolución de llamada (consulte [POPLISTFUNC](../extensibility/poplistfunc.md) para obtener más información).  
  
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
 [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)