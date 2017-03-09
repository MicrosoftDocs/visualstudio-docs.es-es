---
title: "No se puede copiar el archivo &#39;nombre de archivo&#39; en el directorio de ejecuci&#243;n. &lt;motivo&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cant_copy_to_run_dir"
ms.assetid: 80474e62-7cef-48e9-a7c0-820345d5b591
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# No se puede copiar el archivo &#39;nombre de archivo&#39; en el directorio de ejecuci&#243;n. &lt;motivo&gt;
Este error aparece cuando:  
  
-   Una referencia que tiene la propiedad `CopyLocal` \(vea la ventana Propiedades si la referencia está seleccionada en el Explorador de soluciones\) establecida en `true` no se pudo copiar en el directorio desde el que se ejecuta el proyecto.  
  
-   Una dependencia de una referencia con una propiedad `CopyLocal` establecida en `true` no se pudo copiar en el directorio desde el que se ejecuta el proyecto.  
  
-   No se podrá copiar ningún otro archivo que deba copiarse localmente en el directorio desde el que se ejecuta el proyecto.  
  
 Normalmente, el `reason` citado al final del mensaje de error indicará que el archivo se está usando en otro proceso. Es probable que otro elemento esté bloqueando el archivo en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Es posible que exista un problema relacionado con la compilación de proyectos en el mismo directorio de salida. En este caso, compile los dos proyectos en directorios distintos. Si la compilación se realiza en directorios diferentes, el sistema del proyecto copia todos los ensamblados dependientes en el directorio de salida de un proyecto.  
  
 Al agregar la salida de cualquier proyecto en el que esté trabajando como un elemento del cuadro de herramientas, los diseñadores administrados bloquearán la referencia.  
  
 El sistema del proyecto no podrá actualizar el directorio de salida si la salida se está ejecutando actualmente.  
  
 **Para corregir este error**  
  
-   Compruebe el espacio en disco disponible en el equipo.  
  
-   Compruebe si está alcanzando el límite MAX\_PATH impuesto por el sistema de archivos.  
  
     La situación no impedirá que se compile el proyecto. Sin embargo, puede impedir que el proyecto se ejecute correctamente, ya esta advertencia indica que una copia privada de un ensamblado de referencia no se pudo actualizar correctamente. Aunque puede parecer que el proyecto se ejecuta, puede obtener excepciones de carga de un tipo u otro comportamiento inesperado al ejecutar determinadas rutas de código.  
  
## Vea también  
 [No está en la compilación: Cómo: Establecer la propiedad Copy Local de una referencia](http://msdn.microsoft.com/es-es/dfe2ba13-f27f-4356-a481-ea67d5acacbd)