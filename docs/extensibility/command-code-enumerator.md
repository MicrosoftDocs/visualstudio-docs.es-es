---
title: "Enumerador de c&#243;digo de comando | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "enumerador de código de comando"
  - "origen control complementos, enumeración de código de comando"
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Enumerador de c&#243;digo de comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este enumerador se utiliza en las opciones para el [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) y [SccPopulateList](../extensibility/sccpopulatelist-function.md)para indicar el comando para el que se especifican las opciones.  
  
## Sintaxis  
  
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
  
## Miembros  
 SCC\_COMMAND\_GET  
 Corresponde a la [SccGet](../extensibility/sccget-function.md).  
  
 SCC\_COMMAND\_CHECKOUT  
 Corresponde a la [SccCheckout](../extensibility/scccheckout-function.md).  
  
 SCC\_COMMAND\_CHECKIN  
 Corresponde a la [SccCheckin](../extensibility/scccheckin-function.md).  
  
 SCC\_COMMAND\_UNCHECKOUT  
 Corresponde a la [SccUncheckout](../extensibility/sccuncheckout-function.md).  
  
 SCC\_COMMAND\_ADD  
 Corresponde a la [SccAdd](../extensibility/sccadd-function.md).  
  
 SCC\_COMMAND\_REMOVE  
 Corresponde a la [SccRemove](../extensibility/sccremove-function.md).  
  
 SCC\_COMMAND\_DIFF  
 Corresponde a la [SccDiff](../extensibility/sccdiff-function.md).  
  
 SCC\_COMMAND\_HISTORY  
 Corresponde a la [SccHistory](../extensibility/scchistory-function.md).  
  
 SCC\_COMMAND\_RENAME  
 Corresponde a la [SccRename](../extensibility/sccrename-function.md).  
  
 SCC\_COMMAND\_PROPERTIES  
 Corresponde a la [SccProperties](../extensibility/sccproperties-function.md).  
  
 SCC\_COMMAND\_OPTIONS  
 Corresponde a la [SccSetOption](../extensibility/sccsetoption-function.md).  
  
## Vea también  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)   
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)