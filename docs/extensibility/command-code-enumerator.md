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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e2df7ca11d5e93a3ae43d2a6bd1d7ccf8dfe5aa6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089711"
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

## <a name="members"></a>Miembros
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

## <a name="see-also"></a>Consulte también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
