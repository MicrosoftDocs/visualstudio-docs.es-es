---
title: IActiveScriptError | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptError interface
ms.assetid: c8e0288d-38ff-4145-a7e3-f8cdfb72eefe
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca4d3fe5ff90fc0d116814771308fa599052dba9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576902"
---
# <a name="iactivescripterror"></a>IActiveScriptError
Un objeto que implementa esta interfaz se pasa al método [IActiveScriptSite:: OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md) siempre que el motor de scripting encuentra un error no controlado. A continuación, el host llama a los métodos de este objeto para obtener información sobre el error que se ha producido.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptError::GetExceptionInfo](../../winscript/reference/iactivescripterror-getexceptioninfo.md)|Recupera información sobre un error.|  
|[IActiveScriptError::GetSourcePosition](../../winscript/reference/iactivescripterror-getsourceposition.md)|Recupera la ubicación en el código fuente donde se produjo un error.|  
|[IActiveScriptError::GetSourceLineText](../../winscript/reference/iactivescripterror-getsourcelinetext.md)|Recupera la línea del archivo de código fuente donde se produjo un error.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script (Interfaces)](../../winscript/reference/active-script-interfaces.md)