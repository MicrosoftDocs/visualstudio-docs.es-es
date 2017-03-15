---
title: "Depurar archivos de c&#243;digo fuente, Propiedades comunes, P&#225;ginas de propiedades de Soluci&#243;n (Cuadro de di&#225;logo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.options.FindSource"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Depurar archivos de código fuente (página de propiedades)"
  - "depurar [Visual Studio], especificar archivos de código fuente y de símbolos"
  - "archivos de código fuente, especificar en el depurador"
  - "depurador, archivos de origen"
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Depurar archivos de c&#243;digo fuente, Propiedades comunes, P&#225;ginas de propiedades de Soluci&#243;n (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta página de propiedades especifica si el depurador buscará archivos de código fuente al depurar la solución.  
  
 Para obtener acceso a la página de propiedades **Depurar archivos de código fuente**, en el **Explorador de soluciones**, haga clic con el botón secundario en la Solución y, a continuación, seleccione **Propiedades** en el menú contextual.  Expanda la carpeta **Propiedades comunes** y haga clic en la página **Depurar archivos de código fuente**.  
  
 **Directorios que contienen código fuente**  
 Contiene una lista de directorios en los que el depurador busca archivos de código fuente al depurar la solución.  Los subdirectorios de los directorios especificados también se incluyen en la búsqueda.  
  
 **No busque los siguientes archivos de código fuente**  
 Especifique los nombres de los archivos que no desea que lea el depurador.  Si el depurador encuentra uno de estos archivos en uno de los directorios especificados anteriormente, lo omitirá.  Si aparece el cuadro de diálogo **Buscar código fuente** mientras está depurando y hace clic en **Cancelar**, el archivo que buscaba se agregará a dicha lista y el depurador no seguirá buscándolo.  
  
## Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)