---
title: "SCRIPTPROP_HOSTKEEPALIVE (Propiedad) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# SCRIPTPROP_HOSTKEEPALIVE (Propiedad)
Se utiliza para especificar si el motor de script debe conservarse totalmente funcional si hay referencias excepcionales.  
  
 Utilice [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) para establecer esta propiedad en `true`.  Si esta propiedad se establece en `true`, el motor de script se mantiene totalmente funcional mientras hay por lo menos una referencia excepcional o el motor propio script o a un puntero de `IDispatch` a un objeto JavaScript creado mediante el motor de script.  Cuando esta propiedad se establece en `true`, no debe cerrar explícitamente o restablecer el motor de scripts mediante los métodos de [IActiveScript::Close](../../winscript/reference/iactivescript-close.md) o de [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) .  El inicio de la referencia pasada a un objeto de script cierra el motor de script.  
  
## Sintaxis  
  
```  
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## Requisitos  
 Esta propiedad sólo aparece en la versión de activscp.idl instalado con [!INCLUDE[win8](../../javascript/includes/win8-md.md)], con 2707082 KB para Internet Explorer 8 en [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)], o con 2722913 KB para Internet Explorer 9 en [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] o [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)].