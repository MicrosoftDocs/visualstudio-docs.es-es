---
title: "&lt;mensaje&gt; Este error tambi&#233;n podr&#237;a deberse a la combinaci&#243;n de una referencia de archivo a &#39;&lt;nombreDeArchivo1&gt;&#39; en el proyecto &#39;&lt;nombreDeProyecto1&gt;&#39; con una referencia de archivo a &#39;&lt;nombreDeArchivo2&gt;&#39; en el proyecto &#39;&lt;nombreDeProyecto2&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30970"
  - "vbc30970"
helpviewer_keywords: 
  - "BC30970"
ms.assetid: 81cc4f7b-cc16-46cc-9a49-74980300e158
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;mensaje&gt; Este error tambi&#233;n podr&#237;a deberse a la combinaci&#243;n de una referencia de archivo a &#39;&lt;nombreDeArchivo1&gt;&#39; en el proyecto &#39;&lt;nombreDeProyecto1&gt;&#39; con una referencia de archivo a &#39;&lt;nombreDeArchivo2&gt;&#39; en el proyecto &#39;&lt;nombreDeProyecto2&gt;&#39;
\<mensaje\> Este error también podría deberse a la combinación de una referencia de archivo a '\<nombreDeRutaDeAccesoDeArchivo1\>' en el proyecto '\<nombreDeProyecto1\>' con una referencia de archivo a '\<nombreDeRutaDeAccesoDeArchivo2\>' en el proyecto '\<nombreDeProyecto2\>'.  Si ambos ensamblados son idénticos, intente reemplazar estas referencias para que ambas procedan de la misma ubicación.  
  
 El código del proyecto accede a un miembro de otro proyecto, pero la configuración de la solución no permite que el compilador de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] resuelva la referencia.  
  
 Para acceder a un tipo definido en otro ensamblado, el compilador de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] debe tener una referencia a dicho ensamblado. Debe ser una referencia única y no ambigua, que no produzca referencias circulares entre proyectos.  
  
 **Identificador de error:** BC30970  
  
### Para corregir este error  
  
1.  Determine qué proyecto produce el mejor ensamblado para que el proyecto haga referencia a este. Para tomar esta decisión, puede usar criterios como la facilidad de acceso a archivos y la frecuencia de las actualizaciones.  
  
2.  En las propiedades del proyecto, agregue una referencia al archivo que contiene el ensamblado que define el tipo que está usando.  
  
## Vea también  
 [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)   
 [NO ESTÁ EN LA COMPILACIÓN: Hacer referencia a espacios de nombres y componentes](http://msdn.microsoft.com/es-es/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [NO ESTÁ EN LA COMPILACIÓN: Resolver una referencia cuando muchas variables tienen el mismo nombre](http://msdn.microsoft.com/es-es/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [NO ESTÁ EN LA COMPILACIÓN: Cómo: Agregar o quitar referencias usando el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [NO ESTÁ EN LA COMPILACIÓN Cómo: Modificar las propiedades y los valores de configuración del proyecto](http://msdn.microsoft.com/es-es/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Solucionar problemas de referencias rotas](../ide/troubleshooting-broken-references.md)