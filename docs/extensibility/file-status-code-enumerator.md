---
title: "Enumerador de código de estado de archivo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7957a8b841c34b85983af1aa152af466c469f8e1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="file-status-code-enumerator"></a>Enumerador de código de estado de archivo
El `SccStatus` enumerador contiene valores constantes con nombre que especifican el estado de un archivo en el sistema de control de código fuente. Esta enumeración se usa en la [SccQueryInfo](../extensibility/sccqueryinfo-function.md) y `POPLISTFUNC` función de devolución de llamada (vea [POPLISTFUNC](../extensibility/poplistfunc.md) para obtener más información).  
  
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
 Modificado por el usuario actual en el disco local.  
  
 SCC_STATUS_OUTOTHER  
 Archivo está desprotegido por otro usuario.  
  
 SCC_STATUS_OUTEXCLUSIVE  
 Archivo está desprotegido exclusivamente.  
  
 SCC_STATUS_OUTMULTIPLE  
 Archivo se desprotege por más de un usuario.  
  
 SCC_STATUS_OUTOFDATE  
 El archivo no es la más reciente.  
  
 SCC_STATUS_DELETED  
 Se eliminó el archivo del proyecto.  
  
 SCC_STATUS_LOCKED  
 El archivo está bloqueado; No hay más versiones permitidos.  
  
 SCC_STATUS_MERGED  
 Archivo se ha combinado pero aún no se ha corregido y comprobado.  
  
 SCC_STATUS_SHARED  
 Archivo se comparte entre proyectos.  
  
 SCC_STATUS_PINNED  
 Archivo se comparte en una versión específica.  
  
 SCC_STATUS_MODIFIED  
 Archivo ha sido modificado, divide/infringido.  
  
 SCC_STATUS_OUTBYUSER  
 Archivo se desprotege por el usuario actual.  
  
 SCC_STATUS_NOMERGE  
 Archivo nunca se puede mezclar con y no se debe guardar antes de una operación GET.  
  
 SCC_STATUS_RESERVED_1  
 Reservado para uso interno.  
  
 SCC_STATUS_RESERVED_2  
 Reservado para uso interno.  
  
## <a name="see-also"></a>Vea también  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)