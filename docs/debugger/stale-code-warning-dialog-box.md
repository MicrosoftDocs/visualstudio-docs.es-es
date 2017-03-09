---
title: "Advertencia de c&#243;digo obsoleto (Cuadro de di&#225;logo) | Microsoft Docs"
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
  - "vs.debug.ENC.stalecode"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Advertencia de código obsoleto (cuadro de diálogo)"
  - "código, advertencia de código obsoleto"
  - "advertencias, cuadro de diálogo Advertencia de código obsoleto"
  - "Editar y continuar, código obsoleto"
ms.assetid: 594b894c-e652-4e13-a980-9909473d5712
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Advertencia de c&#243;digo obsoleto (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este cuadro de diálogo aparece cuando se han realizado cambios en el código nativo que **Editar y continuar** no pudo aplicar inmediatamente.  Por tanto, parte del código nativo en el marco de pila actual no está actualizado, es decir, que está obsoleto.  Para obtener más información, vea [How to: Work with Stale Code](http://msdn.microsoft.com/es-es/c7536e95-66a6-44a0-995d-3fe5035250b4).  
  
 **No volver a mostrar este cuadro de diálogo**  
 Si activa esta casilla, la función Editar y continuar aplicará los cambios en el código sin pedir permiso en el futuro.  Para volver a activar esta advertencia, vaya al cuadro de diálogo **Opciones**, abra la carpeta **Depuración**, haga clic en la página **Editar y continuar** y seleccione **Avisar cuando haya código obsoleto**.  
  
## Vea también  
 [Cambios y limitaciones admitidos en el código \(C\+\+\)](../debugger/supported-code-changes-cpp.md)   
 [Editar y continuar, Depuración, Opciones \(Cuadro de diálogo\)](../Topic/Edit%20and%20Continue,%20Debugging,%20Options%20Dialog%20Box.md)