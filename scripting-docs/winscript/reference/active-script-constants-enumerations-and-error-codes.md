---
title: "Active Script (constantes, enumeraciones y c&#243;digos de error) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Active Script (constantes, enumeraciones y c&#243;digos de error)
Esta sección describe las enumeraciones y los códigos de error utilizados en los motores de scripting de Windows.  
  
## Constantes  
  
|Constante|Descripción|  
|---------------|-----------------|  
|[Constantes SCRIPTTHREADID](../../winscript/reference/scriptthreadid-constants.md)|Especifica el tipo de subproceso.|  
  
## Propiedades  
  
|Propiedad.|Descripción|  
|----------------|-----------------|  
|[SCRIPTPROP\_HOSTKEEPALIVE \(Propiedad\)](../../winscript/reference/scriptprop-hostkeepalive-property.md)|Se utiliza para especificar si el motor de script debe conservarse totalmente funcional si hay referencias excepcionales.|  
  
## Enumeraciones  
  
|Enumeración|Descripción|  
|-----------------|-----------------|  
|[SCRIPTGCTYPE \(Enumeración\)](../../winscript/reference/scriptgctype-enumeration.md)|El tipo de recolección de elementos no utilizados a realizar.|  
|[SCRIPTLANGUAGEVERSION \(Enumeración\)](../../winscript/reference/scriptlanguageversion-enumeration.md)|Especifica las versiones del script.|  
|[SCRIPTSTATE \(Enumeración\)](../../winscript/reference/scriptstate-enumeration.md)|Especifica el estado de un motor de script.|  
|||  
|[SCRIPTTHREADSTATE \(Enumeración\)](../../winscript/reference/scriptthreadstate-enumeration.md)|Especifica el estado de un subproceso en un motor de script.|  
|[SCRIPTTRACEINFO \(Enumeración\)](../../winscript/reference/scripttraceinfo-enumeration.md)|Representa el evento de script se está realizando paso a paso que.  Utilizado en [IActiveScriptSiteTraceInfo::SendScriptTraceInfo \(Método\)](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).|  
|[SCRIPTUICHANDLING \(Enumeración\)](../../winscript/reference/scriptuichandling-enumeration.md)|Representa la manera en que el control de IU debe controlar.|  
|[SCRIPTUICITEM \(Enumeración\)](../../winscript/reference/scriptuicitem-enumeration.md)|Representa el tipo de elemento de la interfaz de usuario.  Utilizado en [IActiveScriptSiteUIControl::GetUIBehavior \(Método\)](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).|  
  
## Códigos de error  
  
|Código de error|Descripción|  
|---------------------|-----------------|  
|[SCRIPT\_E\_PROPAGATE \(Código de error\)](../../winscript/reference/script-e-propagate-error-code.md)|Un error de script se está propagando al llamador, que podría estar en un subproceso diferente.|  
|[SCRIPT\_E\_RECORDED \(Código de error\)](../../winscript/reference/script-e-recorded-error-code.md)|Un error se pasa entre el motor de script y el host.|  
|[SCRIPT\_E\_REPORTED \(Código de error\)](../../winscript/reference/script-e-reported-error-code.md)|El motor de script informa una excepción no controlada al host.|  
  
## Vea también  
 [Active Script \(Interfaces\)](../../winscript/reference/active-script-interfaces.md)