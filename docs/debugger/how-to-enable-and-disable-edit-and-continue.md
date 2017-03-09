---
title: "C&#243;mo: Habilitar y deshabilitar Editar y continuar | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "/INCREMENTAL (opción del vinculador)"
  - "Aplicar cambios en el código (comando)"
  - "modo de interrupción, aplicar cambios del código"
  - "cambios en el código, aplicar en modo de interrupción"
  - "Editar y continuar, aplicar cambios del código"
  - "Editar y continuar, deshabilitar"
  - "Editar y continuar, habilitar"
  - "Ir (comando)"
  - "INCREMENTAL (opción del vinculador)"
  - "Paso a paso (comando)"
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
caps.latest.revision: 26
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Habilitar y deshabilitar Editar y continuar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede deshabilitar o habilitar Editar y continuar en el cuadro de diálogo **Opciones** en tiempo de diseño.  No puede cambiar este valor mientras esté depurando.  
  
 Editar y continuar solo funciona en las compilaciones de depuración.  En C\+\+ nativo, Editar y continuar requiere el uso de la opción \/INCREMENTAL.  
  
## Procedimientos  
  
#### Para habilitar o deshabilitar Editar y continuar  
  
1.  En el menú **Herramientas**, haga clic en **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones**, abra el nodo **Depuración** y seleccione la categoría **Editar y continuar**.  
  
3.  Para habilitarla, active la casilla **Habilitar Editar y continuar**.  Para deshabilitarla, desactive la casilla.  
  
    > [!NOTE]
    >  Si se habilita IntelliTrace y se recopilan eventos de IntelliTrace e información de llamadas, se deshabilita Editar y continuar.  Para obtener más información, vea [Configurar IntelliTrace para recopilar información de depuración](http://msdn.microsoft.com/es-es/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
4.  Haga clic en **Aceptar**.  
  
## Vea también  
 [Editar y continuar](../debugger/edit-and-continue.md)   
 [Editar y continuar, Depuración, Opciones \(Cuadro de diálogo\)](../Topic/Edit%20and%20Continue,%20Debugging,%20Options%20Dialog%20Box.md)