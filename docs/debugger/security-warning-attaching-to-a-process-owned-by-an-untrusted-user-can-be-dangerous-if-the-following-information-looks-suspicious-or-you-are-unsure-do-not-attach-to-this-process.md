---
title: "Advertencia de seguridad: adjuntar a un proceso que pertenezca a una cuenta de usuario que no sea de confianza puede ser peligroso. Si la informaci&#243;n siguiente le resulta sospechosa o no est&#225; seguro de su procedencia, no la adjunte a este proceso. | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.attachsecuritywarning"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Advertencia de seguridad: adjuntar a un proceso que pertenezca a una cuenta de usuario que no sea de confianza puede ser peligroso. Si la informaci&#243;n siguiente le resulta sospechosa o no est&#225; seguro de su procedencia, no la adjunte a este proceso.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este cuadro de diálogo de advertencia aparece cuando se asocia a un proceso que contiene código de confianza parcial o que pertenece a un usuario que no es de confianza, inmediatamente antes de que ocurra la asociación.  Un proceso que no es de confianza y que contiene código malintencionado puede dañar el equipo que lleva a cabo la depuración.  Si existen razones para desconfiar del proceso, debe hacer clic en **Cancelar** para evitar la depuración.  
  
 Para suprimir esta advertencia al depurar un escenario legítimo, cierre Visual Studio y establezca el valor de esta clave del Registro en 1: el `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning` y, continuación, reinicie Visual Studio.  Cuando termine de depurar el escenario, restablezca el valor a 0, y reinicie Visual Studio.  
  
 Entre los "usuarios de confianza" se encuentra usted, además de un conjunto de usuarios estándar que normalmente se definen en equipos que tienen instalado .NET Framework, como es el caso de `aspnet`, `localsystem`, `networkservice` y `localservice`.  
  
## Lista de UIElement  
 Nombre  
 Nombre del ensamblado que se solicitó depurar  
  
 Usuario  
 Usuario actual  
  
 Attach  
 Presione este botón para seguir depurando mediante asociación  
  
 No adjuntar  
 No se asocia al proceso  
  
## Vea también  
 [Crear asociaciones con procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)