---
title: Enumerador de código de comando | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 06f1a3f7146125e59d02efc72a4d4fc9ab33be39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184388"
---
# <a name="command-code-enumerator"></a>Enumerador de código de comando
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este enumerador se usa en las opciones de [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) y [SccPopulateList](../extensibility/sccpopulatelist-function.md)para indicar el comando para el que se especifican las opciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
enum SCCCOMMAND {  
   SCC_COMMAND_GET,  
   SCC_COMMAND_CHECKOUT,  
   SCC_COMMAND_CHECKIN,  
   SCC_COMMAND_UNCHECKOUT,  
   SCC_COMMAND_ADD,  
   SCC_COMMAND_REMOVE,  
   SCC_COMMAND_DIFF,  
   SCC_COMMAND_HISTORY,  
   SCC_COMMAND_RENAME,  
   SCC_COMMAND_PROPERTIES,  
   SCC_COMMAND_OPTIONS  
};  
```  
  
## <a name="members"></a>Miembros  
 SCC_COMMAND_GET  
 Corresponde a [SccGet](../extensibility/sccget-function.md).  
  
 SCC_COMMAND_CHECKOUT  
 Corresponde a [SccCheckout](../extensibility/scccheckout-function.md).  
  
 SCC_COMMAND_CHECKIN  
 Corresponde a [SccCheckin](../extensibility/scccheckin-function.md).  
  
 SCC_COMMAND_UNCHECKOUT  
 Corresponde a [SccUncheckout](../extensibility/sccuncheckout-function.md).  
  
 SCC_COMMAND_ADD  
 Corresponde a [SccAdd](../extensibility/sccadd-function.md).  
  
 SCC_COMMAND_REMOVE  
 Corresponde a [SccRemove](../extensibility/sccremove-function.md).  
  
 SCC_COMMAND_DIFF  
 Corresponde a [SccDiff](../extensibility/sccdiff-function.md).  
  
 SCC_COMMAND_HISTORY  
 Corresponde a [SccHistory](../extensibility/scchistory-function.md).  
  
 SCC_COMMAND_RENAME  
 Corresponde a [SccRename](../extensibility/sccrename-function.md).  
  
 SCC_COMMAND_PROPERTIES  
 Corresponde a [SccProperties](../extensibility/sccproperties-function.md).  
  
 SCC_COMMAND_OPTIONS  
 Corresponde a [SccSetOption](../extensibility/sccsetoption-function.md).  
  
## <a name="see-also"></a>Consulte también  
 [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)   
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)
