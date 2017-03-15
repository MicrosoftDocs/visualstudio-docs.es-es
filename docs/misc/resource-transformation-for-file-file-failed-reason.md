---
title: "Resource transformation for file &#39;file&#39; failed. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.resx_generator_failed"
ms.assetid: 6b537d38-1da9-4f5f-9ae9-1f26e260c2ac
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Resource transformation for file &#39;file&#39; failed. &lt;reason&gt;
El procesador de recursos utilizado para transformar archivos .resx en archivos .resources binarios falla por algún motivo.  El motivo específico \(si existe\) se adjunta al final de la cadena.  El proceso de compilación no finalizará correctamente si ocurre este error.  
  
 Es muy probable que este error esté causado por un archivo .RESX erróneo.  Por ejemplo, el archivo se puede haber abierto y modificado en un editor de texto.  
  
 Si la \<causa\> que recibe es "Ya se ha agregado el elemento.  Clave en el diccionario: Nombre\_del\_nuevo\_control. \<Nombre de la propiedad\>' Clave agregada: 'Nombre\_del\_control. \<Nombre de la propiedad\>', lea los pasos siguientes para reproducir y corregir el error.  
  
### Para reproducir este error  
  
1.  Cree una nueva aplicación para Windows.  De manera predeterminada, se crea Form1.  
  
2.  En el menú **Ver**, haga clic en **Propiedades**.  
  
3.  En la ventana **Propiedades**, establezca la propiedad **Localizable** en `True`.  
  
4.  En las ventanas **Propiedades**, haga clic en **Idioma**y, a continuación, establezca el valor en "Japonés".  
  
5.  Arrastre un control Button desde el Cuadro de herramientas hasta el formulario.  
  
6.  Cambie el nombre del botón de "Button1" a "BUTTON1".  
  
7.  En el menú **Compilar**, haga clic en **Compilar solución**.  
  
### Para corregir este error  
  
1.  En el menú **Archivo**, haga clic en **Abrir** y, a continuación, haga clic en **Archivo**.  
  
2.  Busque el archivo Form1.resx y, a continuación, haga clic en **Aceptar**.  Aparecerá Form1.resx.  
  
3.  Busque los valores de clave originales y elimínelos manualmente de la lista de datos.  Por ejemplo, hay un botón denominado "Button1."  Ha modificado el nombre de este botón a "BUTTON1".  Los valores de clave para "Button1" y "BUTTON1" están en Form1.resx.  Quite todas las entradas de "Button1" y, a continuación, recompila el proyecto.  
  
## Vea también  
 [Resources in .Resx File Format](http://msdn.microsoft.com/es-es/0c476133-87e4-47e8-b0ef-4b88f4ef3dc5)   
 [File Types and File Extensions in Visual Basic and Visual C\#](http://msdn.microsoft.com/es-es/f793852c-da06-4d52-a826-65f635844772)