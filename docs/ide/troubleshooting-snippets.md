---
title: "Solucionar problemas con fragmentos de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fragmentos de código de IntelliSense, solucionar problemas"
  - "solucionar problemas de fragmentos de código de IntelliSense"
  - "solucionar problemas de Visual Basic, fragmentos de código de IntelliSense"
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Solucionar problemas con fragmentos de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Hay dos problemas que se producen habitualmente con los fragmentos de código de IntelliSense: un archivo del miniprograma está dañado o el contenido del archivo del miniprograma no es válido.  
  
## Problemas comunes  
  
### El miniprograma no se desde el archivo Explorador arrastrando un archivo de código fuente de Visual Studio  
  
-   El código XML del archivo del miniprograma puede estar dañado.  El **Editor XML** de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] puede buscar los problemas en la estructura XML.  
  
-   El archivo del miniprograma no puede ajustarse al esquema del miniprograma.  El **Editor XML** de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] puede buscar los problemas en la estructura XML.  
  
### El código tiene errores de compilación que no aparecen resaltados  
  
-   Quizás falte una referencia de proyecto.  Examine la documentación sobre el miniprograma.  Si la referencia no se encuentra en el equipo, deberá instalarla.  Al insertar un miniprograma, debe agregar al proyecto todas las referencias necesarias.  Si el miniprograma no contiene la información de referencia, se puede notificar al creador del miniprograma como un error.  
  
-   Es posible que una variable no esté definida.  Las variables indefinidas de un miniprograma deberían aparecer resaltadas.  Si esto no ocurre, se le puede notificar al creador del miniprograma como un error.  
  
## Vea también  
 [Fragmentos de código](../ide/code-snippets.md)