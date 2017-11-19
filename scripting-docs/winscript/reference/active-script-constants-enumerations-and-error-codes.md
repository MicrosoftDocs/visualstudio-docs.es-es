---
title: "Active Script constantes, enumeraciones y códigos de Error | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb4165a5471c8e79827f0f7605cef575e82bab75
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="active-script-constants-enumerations-and-error-codes"></a>Active Script (constantes, enumeraciones y códigos de error)
Esta sección describen las enumeraciones y códigos de error usados en los motores de Scripting de Windows.  
  
## <a name="constants"></a>Constantes  
  
|Constante|Descripción|  
|--------------|-----------------|  
|[SCRIPTTHREADID (Constantes)](../../winscript/reference/scriptthreadid-constants.md)|Especifica el tipo de subproceso.|  
  
## <a name="properties"></a>Propiedades  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|[SCRIPTPROP_HOSTKEEPALIVE (Propiedad)](../../winscript/reference/scriptprop-hostkeepalive-property.md)|Se utiliza para especificar si se permite o no el motor de scripting se debe mantener totalmente funcional si hay referencias pendientes.|  
  
## <a name="enumerations"></a>Enumeraciones  
  
|Enumeración|Descripción|  
|-----------------|-----------------|  
|[SCRIPTGCTYPE (Enumeración)](../../winscript/reference/scriptgctype-enumeration.md)|El tipo de colección de elementos no utilizados para realizar.|  
|[SCRIPTLANGUAGEVERSION (Enumeración)](../../winscript/reference/scriptlanguageversion-enumeration.md)|Especifica las posibles secuencias de comandos de versiones.|  
|[SCRIPTSTATE (Enumeración)](../../winscript/reference/scriptstate-enumeration.md)|Especifica el estado de un motor de scripting.|  
|||  
|[SCRIPTTHREADSTATE (Enumeración)](../../winscript/reference/scriptthreadstate-enumeration.md)|Especifica el estado de un subproceso de un motor de scripting.|  
|[SCRIPTTRACEINFO (Enumeración)](../../winscript/reference/scripttraceinfo-enumeration.md)|Representa el evento de secuencia de comandos que se realiza un seguimiento. Utilizado en el [método iactivescriptsitetraceinfo:: Sendscripttraceinfo](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).|  
|[SCRIPTUICHANDLING (Enumeración)](../../winscript/reference/scriptuichandling-enumeration.md)|Representa la manera en que se debería tratar el control de interfaz de usuario.|  
|[SCRIPTUICITEM (Enumeración)](../../winscript/reference/scriptuicitem-enumeration.md)|Representa el tipo de elemento de interfaz de usuario. Utilizado en el [iactivescriptsiteuicontrol:: Getuibehavior (método)](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).|  
  
## <a name="error-codes"></a>Códigos de error  
  
|Código de error|Descripción|  
|----------------|-----------------|  
|[SCRIPT_E_PROPAGATE (Código de error)](../../winscript/reference/script-e-propagate-error-code.md)|Un error de script se propaga al llamador, que podría estar en un subproceso diferente.|  
|[SCRIPT_E_RECORDED (Código de error)](../../winscript/reference/script-e-recorded-error-code.md)|Se ha pasado un error entre el motor de scripts y el host.|  
|[SCRIPT_E_REPORTED (Código de error)](../../winscript/reference/script-e-reported-error-code.md)|El motor de scripting ha informado de una excepción no controlada en el host.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script (Interfaces)](../../winscript/reference/active-script-interfaces.md)