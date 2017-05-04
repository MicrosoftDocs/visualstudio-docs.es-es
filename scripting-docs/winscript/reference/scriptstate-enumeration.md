---
title: "SCRIPTSTATE (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTSTATE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SCRIPTSTATE (enum)"
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# SCRIPTSTATE (Enumeraci&#243;n)
Especifica el estado de un motor de script.  Esta enumeración es utilizada por los métodos de [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) , de [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) , y de [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .  
  
## Sintaxis  
  
```  
typedef enum tagSCRIPTSTATE {  
    SCRIPTSTATE_UNINITIALIZED = 0,  
    SCRIPTSTATE_INITIALIZED   = 5,  
    SCRIPTSTATE_STARTED       = 1,  
    SCRIPTSTATE_CONNECTED     = 2,  
    SCRIPTSTATE_DISCONNECTED  = 3,  
    SCRIPTSTATE_CLOSED        = 4  
} SCRIPTSTATE;  
```  
  
## Valores de enumeración  
  
|||  
|-|-|  
|SCRIPTSTATE\_UNINITIALIZED|El script termina de crearse, pero todavía no se ha inicializado con una interfaz y [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) de `IPersist*` .|  
|SCRIPTSTATE\_INITIALIZED|El script se ha inicializado, pero no se está ejecutando \(conectando con otros objetos o eventos de contraer\) ni está ejecutando ningún codificados.  El código se puede consultar la ejecución llamando al método de [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md) .|  
|SCRIPTSTATE\_STARTED|El script se puede ejecutar código, pero todavía no se hundiendo los eventos de objetos agregados por el método de [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .|  
|SCRIPTSTATE\_CONNECTED|El script se carga y conectado para los eventos de contraer.|  
|SCRIPTSTATE\_DISCONNECTED|El script se carga y tiene un estado de la ejecución en tiempo de ejecución, pero es temporalmente desconectada de eventos de contraer.|  
|SCRIPTSTATE\_CLOSED|El script se ha cerrado.  El motor de script funciona y ya no devuelve errores para la mayoría de los métodos.|  
  
## Vea también  
 [Active Script \(constantes, enumeraciones y códigos de error\)](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)