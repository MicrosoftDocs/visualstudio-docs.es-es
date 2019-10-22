---
title: IDebugStackFrame (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrame interface
ms.assetid: e95c1b4f-17c1-490c-a56b-c25fa45d4822
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8f645d6460ff15734348267b5138b1b6edea071
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63005883"
---
# <a name="idebugstackframe-interface"></a>IDebugStackFrame (Interfaz)
Representa un marco de pila lógico en la pila de subprocesos. Llame a la `IDebugStackFrame::QueryInterface` método para obtener el `IDebugExpressionContext` interfaz, que permite las ventanas inspección y evaluación de expresión.  
  
 Además de los métodos heredados de `IUnknown`, el `IDebugStackFrame` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|Devuelve el contexto de código actual asociado con el marco de pila.|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|Devuelve una descripción de texto largos o corta del marco de pila.|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|Devuelve una descripción de texto largos o corta del lenguaje.|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|Devuelve el subproceso asociado a este marco de pila.|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|Devuelve un explorador de propiedades para el marco actual.|