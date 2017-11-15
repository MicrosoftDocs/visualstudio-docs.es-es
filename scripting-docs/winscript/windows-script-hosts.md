---
title: Hosts de Windows Script | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Windows Script Host, implementing hosts
ms.assetid: 9d5f6471-b318-40f3-be01-d9cd0b1cdd47
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41fa898c7f0d62cd35cc1cb1c7b35eb2651c8bb6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="windows-script-hosts"></a>Windows Script (Hosts)
Al implementar el host de Microsoft Windows Script, puede suponer de forma segura que un motor de scripting solo llama a la interfaz [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) en el contexto del subproceso base siempre y cuando el host haga lo siguiente:  
  
-   Elija un subproceso base (por lo general, el que contiene el bucle de mensajes).  
  
-   Cree una instancia del motor de scripting en el subproceso base.  
  
-   Llame a los métodos del motor de scripts solo desde el subproceso base, excepto si se permite específicamente, como en los casos de [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) y [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md).  
  
-   Llame al objeto de distribución del motor de scripts solo desde el subproceso base.  
  
-   Garantice que el bucle de mensajes se ejecute en el subproceso base si se proporciona un controlador de ventana.  
  
-   Garantice que los objetos del objeto del host solo modelen eventos de origen en el subproceso base.  
  
 Todos los hosts de subproceso único siguen estas reglas automáticamente. El modelo restringido descrito anteriormente se relaja intencionadamente lo bastante como para permitir que un host anule un script detenido mediante la llamada a [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) desde otro subproceso (iniciado por un controlador CTRL+BREAK o similar), o que duplique un script en un nuevo subproceso mediante [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md).  
  
## <a name="remarks"></a>Comentarios  
 Ninguna de estas restricciones se aplica a un host que elija implementar una interfaz [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) sin subprocesos y un modelo de objetos sin subprocesos. Un host de este tipo puede usar la interfaz [IActiveScript](../winscript/reference/iactivescript.md) desde cualquier subproceso, sin restricciones.  
  
## <a name="see-also"></a>Vea también  
 [Windows Script (Interfaces)](../winscript/windows-script-interfaces.md)