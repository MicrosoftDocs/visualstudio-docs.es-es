---
title: Constantes, enumeraciones y códigos de error de Active script | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e03bef99c2297d517aa5234db49820a2b9600ce7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572711"
---
# <a name="active-script-constants-enumerations-and-error-codes"></a>Active Script (constantes, enumeraciones y códigos de error)
En esta sección se describen las enumeraciones y los códigos de error que se usan en los motores de Windows Scripting.  
  
## <a name="constants"></a>Constantes  
  
|Constante|Descripción|  
|--------------|-----------------|  
|[SCRIPTTHREADID (Constantes)](../../winscript/reference/scriptthreadid-constants.md)|Especifica el tipo de subproceso.|  
  
## <a name="properties"></a>Propiedades  
  
|Propiedad.|Descripción|  
|--------------|-----------------|  
|[SCRIPTPROP_HOSTKEEPALIVE (Propiedad)](../../winscript/reference/scriptprop-hostkeepalive-property.md)|Se utiliza para especificar si el motor de scripting debe mantenerse totalmente funcional si hay referencias pendientes.|  
  
## <a name="enumerations"></a>Enumeraciones  
  
|Enumeración|Descripción|  
|-----------------|-----------------|  
|[SCRIPTGCTYPE (Enumeración)](../../winscript/reference/scriptgctype-enumeration.md)|Tipo de recolección de elementos no utilizados que se va a realizar.|  
|[SCRIPTLANGUAGEVERSION (Enumeración)](../../winscript/reference/scriptlanguageversion-enumeration.md)|Especifica las versiones de scripting posibles.|  
|[SCRIPTSTATE (Enumeración)](../../winscript/reference/scriptstate-enumeration.md)|Especifica el estado de un motor de scripting.|  
|||  
|[SCRIPTTHREADSTATE (Enumeración)](../../winscript/reference/scriptthreadstate-enumeration.md)|Especifica el estado de un subproceso en un motor de scripting.|  
|[SCRIPTTRACEINFO (Enumeración)](../../winscript/reference/scripttraceinfo-enumeration.md)|Representa el evento de script del que se realiza un seguimiento. Se usa en el [método IActiveScriptSiteTraceInfo:: sendscripttraceinfo (](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).|  
|[SCRIPTUICHANDLING (Enumeración)](../../winscript/reference/scriptuichandling-enumeration.md)|Representa la forma en que se debe controlar el control de interfaz de usuario.|  
|[SCRIPTUICITEM (Enumeración)](../../winscript/reference/scriptuicitem-enumeration.md)|Representa el tipo de elemento de interfaz de usuario. Se usa en el [método IActiveScriptSiteUIControl:: getuibehavior (](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).|  
  
## <a name="error-codes"></a>Códigos de error  
  
|Código de error|Descripción|  
|----------------|-----------------|  
|[SCRIPT_E_PROPAGATE (Código de error)](../../winscript/reference/script-e-propagate-error-code.md)|Se propagará un error de script al autor de la llamada, que podría estar en un subproceso diferente.|  
|[SCRIPT_E_RECORDED (Código de error)](../../winscript/reference/script-e-recorded-error-code.md)|Se ha pasado un error entre el motor de scripts y el host.|  
|[SCRIPT_E_REPORTED (Código de error)](../../winscript/reference/script-e-reported-error-code.md)|El motor de scripting ha detectado una excepción no controlada en el host.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script (Interfaces)](../../winscript/reference/active-script-interfaces.md)