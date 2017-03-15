---
title: "Could not transform licenses file &#39;file&#39; into a binary resource. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.licx_generator_failed"
ms.assetid: 875e948c-d7a3-4ffc-be0d-f341de5f6310
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not transform licenses file &#39;file&#39; into a binary resource. &lt;reason&gt;
El procesador de licencias utilizado para transformar archivos .licx en archivos binarios falla por algún motivo.  
  
 Normalmente, este error está provocado por un archivo .licx erróneo.  Por ejemplo, el archivo se puede haber abierto y modificado en un editor de texto.  
  
 El proceso de compilación no finalizará correctamente si ocurre este error.  
  
### Para corregir este error  
  
1.  Seleccione el proyecto en el Explorador de soluciones.  
  
2.  Haga clic en **Mostrar todos los archivos** en el menú **Proyecto**.  
  
3.  En el Explorador de soluciones, expanda la carpeta obj y, a continuación, la carpeta **Debug**.  
  
4.  Busque el archivo denominado "miAplicación.exe.licenses", donde miAplicación es el nombre de la aplicación de Windows Forms.  
  
5.  Elimine este archivo y recompile la solución.  
  
## Vea también  
 [How to: License Components and Controls](../Topic/How%20to:%20License%20Components%20and%20Controls.md)