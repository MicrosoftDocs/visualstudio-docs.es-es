---
title: Enumerador de código de comandos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 97b856b0c22631b3e4f9b8860f9aaba728e6944d
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315500"
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
[Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)  
[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
[SccPopulateList](../extensibility/sccpopulatelist-function.md)
