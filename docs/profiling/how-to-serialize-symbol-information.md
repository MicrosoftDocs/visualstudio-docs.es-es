---
title: "C&#243;mo: Serializar la informaci&#243;n de s&#237;mbolos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Performance.General"
helpviewer_keywords: 
  - "herramientas de generación de perfiles, serializar la información de símbolos"
  - "herramientas de rendimiento, serializar la información de símbolos"
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# C&#243;mo: Serializar la informaci&#243;n de s&#237;mbolos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede serializar símbolos que tiene que tener para analizar la aplicación.  La serialización de símbolos agrega símbolos al archivo .vsp.  Al agregar información de símbolos al archivo .vsp, otras personas pueden analizar el informe de rendimiento sin necesidad de obtener acceso a los símbolos originales.  Si no se serializan los símbolos, necesita los archivos .exe y .pdb instrumentados originales para analizar el archivo .vsp.  
  
### Para serializar automáticamente información de símbolos  
  
1.  En el menú **Herramientas**, haga clic en **Opciones**.  
  
     Aparecerá el cuadro de diálogo **Opciones**.  
  
2.  Haga clic en **Herramientas de rendimiento**.  
  
3.  En **Configuración general**, seleccione **Serializar información de símbolos automáticamente**.  
  
## Vea también  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [Cómo: Hacer referencia a información de símbolos de Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [How to: Save Analyzed Report Files](http://msdn.microsoft.com/es-es/0340ddde-caf4-48ac-8af3-d15dcdade556)