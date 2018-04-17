---
title: Comando código enumerador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5ba40c0506bdeecc7d6438f83f2d4342c62cc2e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="command-code-enumerator"></a>Enumerador de código de comando
Este enumerador se utiliza en las opciones para la [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) y [SccPopulateList](../extensibility/sccpopulatelist-function.md)para indicar el comando para el que se especifican las opciones.  
  
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
 Corresponde a la [SccGet](../extensibility/sccget-function.md).  
  
 SCC_COMMAND_CHECKOUT  
 Corresponde a la [SccCheckout](../extensibility/scccheckout-function.md).  
  
 SCC_COMMAND_CHECKIN  
 Corresponde a la [SccCheckin](../extensibility/scccheckin-function.md).  
  
 SCC_COMMAND_UNCHECKOUT  
 Corresponde a la [SccUncheckout](../extensibility/sccuncheckout-function.md).  
  
 SCC_COMMAND_ADD  
 Corresponde a la [SccAdd](../extensibility/sccadd-function.md).  
  
 SCC_COMMAND_REMOVE  
 Corresponde a la [SccRemove](../extensibility/sccremove-function.md).  
  
 SCC_COMMAND_DIFF  
 Corresponde a la [SccDiff](../extensibility/sccdiff-function.md).  
  
 SCC_COMMAND_HISTORY  
 Corresponde a la [SccHistory](../extensibility/scchistory-function.md).  
  
 SCC_COMMAND_RENAME  
 Corresponde a la [SccRename](../extensibility/sccrename-function.md).  
  
 SCC_COMMAND_PROPERTIES  
 Corresponde a la [SccProperties](../extensibility/sccproperties-function.md).  
  
 SCC_COMMAND_OPTIONS  
 Corresponde a la [SccSetOption](../extensibility/sccsetoption-function.md).  
  
## <a name="see-also"></a>Vea también  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)   
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)