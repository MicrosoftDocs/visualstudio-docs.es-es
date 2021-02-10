---
title: Enumerador de código de comando | Microsoft Docs
description: El enumerador de código de comando se usa en las opciones de SccGetCommandOptions y SccPopulateListto para indicar el comando para el que se especifican las opciones.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2911a39c15fa259057e0b7b48d79e142cda34094
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938256"
---
# <a name="command-code-enumerator"></a>Enumerador de código de comando
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

## <a name="members"></a>Members
SCC_COMMAND_GET corresponde a [SccGet](../extensibility/sccget-function.md).

SCC_COMMAND_CHECKOUT corresponde a [SccCheckout](../extensibility/scccheckout-function.md).

SCC_COMMAND_CHECKIN corresponde a [SccCheckin](../extensibility/scccheckin-function.md).

SCC_COMMAND_UNCHECKOUT corresponde a [SccUncheckout](../extensibility/sccuncheckout-function.md).

SCC_COMMAND_ADD corresponde a [SccAdd](../extensibility/sccadd-function.md).

SCC_COMMAND_REMOVE corresponde a [SccRemove](../extensibility/sccremove-function.md).

SCC_COMMAND_DIFF corresponde a [SccDiff](../extensibility/sccdiff-function.md).

SCC_COMMAND_HISTORY corresponde a [SccHistory](../extensibility/scchistory-function.md).

SCC_COMMAND_RENAME corresponde a [SccRename](../extensibility/sccrename-function.md).

SCC_COMMAND_PROPERTIES corresponde a [SccProperties](../extensibility/sccproperties-function.md).

SCC_COMMAND_OPTIONS corresponde a [SccSetOption](../extensibility/sccsetoption-function.md).

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
