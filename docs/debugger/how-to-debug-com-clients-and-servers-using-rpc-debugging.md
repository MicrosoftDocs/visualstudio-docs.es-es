---
title: "C&#243;mo: Depurar clientes y servidores COM mediante la depuraci&#243;n RPC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.com"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "clientes COM, depurar"
  - "servidores COM, depurar"
  - "COM, depurar"
  - "depuración de llamada al procedimiento remoto en proceso"
  - "depuración de llamada al procedimiento remoto en modo inactivo"
  - "depuración remota, RPC (llamada a procedimiento remoto)"
  - "RPC (llamada a procedimiento remoto)"
  - "RPC (llamada a procedimiento remoto), depurar"
  - "RPC (llamada a procedimiento remoto), depurar clientes y servidores COM"
ms.assetid: 3e8526c8-43b5-4b87-8e0d-b22c24f0a3ea
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# C&#243;mo: Depurar clientes y servidores COM mediante la depuraci&#243;n RPC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede utilizar la depuración RPC \(llamada a procedimiento remoto\) para depurar aplicaciones COM cliente\-servidor.  Debe habilitar la depuración RPC para poder utilizarla.  Con la depuración RPC habilitada, cuando entra en la llamada al servidor desde el cliente, el depurador se adjunta al servidor y le permite depurar el código.  Una vez asociado el depurador, podrá utilizar todas sus características con los procesos del servidor y del cliente.  
  
### Para habilitar la depuración RPC  
  
1.  En el menú **Herramientas**, haga clic en **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones**, haga clic en la carpeta **Depuración**.  
  
3.  Haga clic en la página **Nativo**.  
  
4.  Active la casilla **Depuración RPC**.  
  
    > [!NOTE]
    >  Para depurar las llamadas RPC, debe tener privilegios de Administrador o Usuario avanzado.  
  
    > [!NOTE]
    >  La introducción paso a paso de las RPC en un servidor remoto donde se ejecuta Microsoft Windows Vista sólo funcionará si se asocia un depurador nativo al servidor remoto.  De lo contrario, se producirá un error en la llamada RPC sin que se muestre ningún mensaje de error.  Si no, se completará la llamada RPC, pero no funcionará la ejecución paso a paso en la llamada RPC.  
  
## Vea también  
 [Depuración de servidores y contenedores COM](../debugger/com-server-and-container-debugging.md)   
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)