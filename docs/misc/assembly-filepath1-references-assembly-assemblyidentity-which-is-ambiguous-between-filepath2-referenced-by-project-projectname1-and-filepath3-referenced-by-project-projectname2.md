---
title: "El ensamblado &#39;&lt;rutaAccesoArchivo1&gt;&#39; hace referencia al ensamblado &#39;&lt;identidadEnsamblado&gt;&#39;, que es ambiguo entre &#39;&lt;rutaAccesoArchivo2&gt;&#39; (al que hace referencia el proyecto &#39;&lt;nombreProyecto1&gt;&#39;) y &#39;&lt;rutaAccesoArchivo3&gt;&#39; (al que hace referencia el proyecto &#39;&lt;nombreProyecto2&gt;&#39;). | Microsoft Docs"
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
  - "bc42204"
  - "vbc42204"
helpviewer_keywords: 
  - "BC42204"
ms.assetid: b0c3d2b6-2776-4981-b79e-2e36f03d4123
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El ensamblado &#39;&lt;rutaAccesoArchivo1&gt;&#39; hace referencia al ensamblado &#39;&lt;identidadEnsamblado&gt;&#39;, que es ambiguo entre &#39;&lt;rutaAccesoArchivo2&gt;&#39; (al que hace referencia el proyecto &#39;&lt;nombreProyecto1&gt;&#39;) y &#39;&lt;rutaAccesoArchivo3&gt;&#39; (al que hace referencia el proyecto &#39;&lt;nombreProyecto2&gt;&#39;).
El ensamblado '\<rutaAccesoArchivo1\>' hace referencia al ensamblado '\<identidadEnsamblado\>', que es ambiguo entre '\<rutaAccesoArchivo2\>' \(al que hace referencia el proyecto '\<nombreProyecto1\>'\) y '\<rutaAccesoArchivo3\>' \(al que hace referencia el proyecto '\<nombreProyecto2\>'\). Se usará '\<rutaAccesoArchivo2\>'. Si ambos ensamblados son idénticos, cambie las referencias a la misma ubicación.  
  
 Un ensamblado accede a un tipo en otro ensamblado al que tiene más de una referencia de archivo.  
  
 El compilador no puede garantizar que los archivos de las diferentes ubicaciones contengan la misma versión del mismo ensamblado. Por lo tanto, las referencias de archivo son ambiguas y el compilador debe seleccionar uno.  
  
 La *identidad del ensamblado* incluye el nombre, la versión, la clave pública, si existe, y la referencia cultural del ensamblado. Esta información identifica de forma exclusiva el ensamblado.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC42204  
  
### Para corregir este error  
  
1.  Determine qué archivo representa la mejor elección para el ensamblado. Puede usar criterios como la versión más reciente, la accesibilidad del archivo y la probabilidad de que se actualice cuando sea apropiado.  
  
2.  Cambie todas las referencias de archivo a este ensamblado para que usen la ruta de acceso de archivo idéntica a su archivo elegido.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Ensamblados](http://msdn.microsoft.com/es-es/6c5c7b30-fa78-4f40-b908-120d0743b0e6)   
 [Ensamblados en Common Language Runtime](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md)   
 [Ventajas de los ensamblados](../Topic/Assembly%20Benefits.md)   
 [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)   
 [NIB: Administrar referencias](http://msdn.microsoft.com/es-es/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB: Cómo: Agregar o quitar referencias usando el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)