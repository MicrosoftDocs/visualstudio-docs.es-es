---
title: "El ensamblado &#39;&lt;rutaDeAccesoDeArchivo1&gt;&#39; hace referencia al ensamblado &#39;&lt;identidadDeEnsamblado&gt;&#39;, que presenta ambig&#252;edad entre &#39;&lt;rutaDeAccesoDeArchivo2&gt;&#39; y &#39;&lt;rutaDeAccesoDeArchivo3&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42205"
  - "bc42205"
helpviewer_keywords: 
  - "BC42205"
ms.assetid: c36feb10-dded-4073-9553-af278ae5560b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El ensamblado &#39;&lt;rutaDeAccesoDeArchivo1&gt;&#39; hace referencia al ensamblado &#39;&lt;identidadDeEnsamblado&gt;&#39;, que presenta ambig&#252;edad entre &#39;&lt;rutaDeAccesoDeArchivo2&gt;&#39; y &#39;&lt;rutaDeAccesoDeArchivo3&gt;&#39;
El ensamblado '\<rutaDeAccesoDeArchivo1\>' hace referencia al ensamblado '\<identidadDeEnsamblado\>', que presenta ambigüedad entre '\<rutaDeAccesoDeArchivo2\>' y '\<rutaDeAccesoDeArchivo3\>'. Se usará '\<rutaDeAccesoDeArchivo2\>'.  
  
 Un ensamblado accede a un tipo en otro ensamblado al que tiene más de una referencia de archivo.  
  
 El compilador no puede garantizar que los archivos de las diferentes ubicaciones contengan la misma versión del mismo ensamblado. Por lo tanto, las referencias de archivo son ambiguas y el compilador debe seleccionar una.  
  
 La *identidad del ensamblado* incluye el nombre, la versión, la clave pública, si existe, y la referencia cultural del ensamblado. Esta información identifica de forma exclusiva el ensamblado.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC42205  
  
### Para corregir este error  
  
1.  Determine qué archivo representa la mejor elección para el ensamblado. Puede usar criterios como la versión más reciente, la accesibilidad del archivo y la probabilidad de que se actualice cuando sea apropiado.  
  
2.  Cambie todas las referencias de archivo a este ensamblado para que usen la ruta de acceso de archivo idéntica al archivo elegido.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Ensamblados](http://msdn.microsoft.com/es-es/6c5c7b30-fa78-4f40-b908-120d0743b0e6)   
 [Ensamblados en Common Language Runtime](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md)   
 [Ventajas de los ensamblados](../Topic/Assembly%20Benefits.md)   
 [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)   
 [NO ESTÁ EN LA COMPILACIÓN: Administrar referencias](http://msdn.microsoft.com/es-es/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NO ESTÁ EN LA COMPILACIÓN: Cómo: Agregar o quitar referencias usando el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)