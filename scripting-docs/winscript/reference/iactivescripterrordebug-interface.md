---
title: IActiveScriptErrorDebug (interfaz) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug interface
ms.assetid: e5d50427-c033-4138-ac6e-3b2dfb3b750a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 936770859d3bdfe81c84245d32ae63346b142a01
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009537"
---
# <a name="iactivescripterrordebug-interface"></a>IActiveScriptErrorDebug (Interfaz)
Proporciona información de contexto de documento para errores de compilación y excepciones de tiempo de ejecución. El `IActiveScriptError::QueryInterface` método admite la `IActiveScriptErrorDebug` interfaz.  
  
 Además de los métodos heredados de `IActiveScriptError`, el `IActiveScriptErrorDebug` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptErrorDebug::GetDocumentContext](../../winscript/reference/iactivescripterrordebug-getdocumentcontext.md)|Proporciona el contexto del documento para este error.|  
|[IActiveScriptErrorDebug::GetStackFrame](../../winscript/reference/iactivescripterrordebug-getstackframe.md)|Proporciona el marco de pila que está en vigor para los errores en tiempo de ejecución.|