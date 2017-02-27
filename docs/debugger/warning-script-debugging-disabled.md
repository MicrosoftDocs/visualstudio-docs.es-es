---
title: "Advertencia: Depuraci&#243;n de script deshabilitada | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.scriptdisabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia: Depuraci&#243;n de script deshabilitada
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La depuración de script está deshabilitada actualmente en Internet Explorer  
  
 Esta advertencia se produce al intentar depurar script sin habilitar la depuración en Internet Explorer.  Por razones de seguridad, Internet Explorer deshabilita de forma predeterminada la depuración de script.  
  
### Para habilitar la depuración de script en Internet Explorer  
  
1.  En el menú **Herramientas** de Internet Explorer, elija **Opciones de Internet**.  
  
2.  En el cuadro de diálogo **Opciones de Internet**, haga clic en la ficha **Opciones avanzadas**.  
  
3.  En la ficha **Opciones avanzadas**, observe la categoría **Examinar** en el cuadro **Configuración**.  
  
4.  Desactive **Deshabilitar la depuración de scripts \(Internet Explorer\)**.  
  
5.  Haga clic en **Aceptar**.  
  
6.  Salga y reinicie Internet Explorer.  
  
     La nueva configuración estará ahora en vigor.  
  
## Vea también  
 [Cómo: Adjuntar a script](../debugger/how-to-attach-to-script.md)