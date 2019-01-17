---
title: IActiveScriptParseProcedure | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParseProcedure interface
ms.assetid: 741a35bb-5b92-489e-ba8a-a406b42125fc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78db05160adef51c414f4c4804f33d47812a9b38
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349548"
---
# <a name="iactivescriptparseprocedure"></a>IActiveScriptParseProcedure
Si el motor de scripts de Windows permite que el texto del código fuente para los procedimientos que se agregarán a la secuencia de comandos, implementa el `IActiveScriptParseProcedure` interfaz. Para los lenguajes de scripting interpretados que no tienen ningún entorno de creación independiente, como VBScript, esto proporciona un mecanismo alternativo (distinto de `IActiveScriptParse` o `IPersist`*) para agregar los procedimientos de script al espacio de nombres.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|||  
|-|-|  
|Método|Descripción|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|Analiza el procedimiento de código especificado y agrega el procedimiento al espacio de nombres.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script (Interfaces)](../../winscript/reference/active-script-interfaces.md)