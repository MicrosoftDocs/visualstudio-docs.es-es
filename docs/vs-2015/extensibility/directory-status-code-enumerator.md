---
title: Enumerador de código de estado de directorio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e082a691a389d5cb9a8fa307a627b11911e0db78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185258"
---
# <a name="directory-status-code-enumerator"></a>Enumerador de código de estado de directorio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El `SccDirStatus` enumerador contiene valores constantes con nombre que especifican el estado de un directorio en el sistema de control de código fuente. Esta enumeración la usa [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Esto se presentó en la versión 1,2 de la API del complemento de control de código fuente.  
  
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
 SCC_DIRSTATUS_INVALID  
 No se pudo obtener el estado. no se base en él.  
  
 SCC_DIRSTATUS_NOTCONTROLLED  
 El directorio no está bajo control de código fuente.  
  
 SCC_DIRSTATUS_CONTROLLED  
 El directorio está bajo control de código fuente.  
  
 SCC_DIRSTATUS_EMPTYPROJ  
 El proyecto correspondiente a este directorio está vacío.  
  
## <a name="see-also"></a>Consulte también  
 [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
