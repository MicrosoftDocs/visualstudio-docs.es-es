---
title: Enumerador de código de estado de directorio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a23bef10dda57d761ce7f07c3b87808b021830c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766654"
---
# <a name="directory-status-code-enumerator"></a>Enumerador de código de estado de directorio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El `SccDirStatus` enumerador contiene valores constantes con nombre que especifican el estado de un directorio en el sistema de control de código fuente. Esta enumeración se utiliza en el [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Esto se introdujo en la versión 1.2 de la API de complemento de Control de código fuente.  
  
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
 No se pudo obtener el estado; No confíe en él.  
  
 SCC_DIRSTATUS_NOTCONTROLLED  
 Directorio no está bajo control de código fuente.  
  
 SCC_DIRSTATUS_CONTROLLED  
 Directorio está bajo control de código fuente.  
  
 SCC_DIRSTATUS_EMPTYPROJ  
 Proyecto correspondiente a este directorio está vacío.  
  
## <a name="see-also"></a>Vea también  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)

