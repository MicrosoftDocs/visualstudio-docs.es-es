---
title: "Codificaciones y saltos de l&#237;nea | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.Encoding"
helpviewer_keywords: 
  - "editores, saltos de línea"
  - "codificar"
  - "caracteres de salto de línea"
  - "saltos de línea"
  - "Visual Studio, codificar"
  - "Visual Studio, caracteres de salto de línea"
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Codificaciones y saltos de l&#237;nea
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En Visual Studio se puede utilizar el  **Opciones para guardar archivo avanzada** configuración para determinar el tipo de salto de línea de caracteres desee.  También puede cambiar la codificación de un archivo con la misma configuración.  
  
> [!NOTE]
>  Si tiene ciertos tipos de configuraciones de desarrollo \(desarrollo de Web, F\#, Visual Basic\) puede que no vea  **Opciones avanzadas para guardar** en el menú.  Para cambiar la configuración \(por ejemplo, en General\), abra  **Herramientas \/ importar y exportar configuraciones**.  For More Information, See  [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 En Visual Studio, los siguientes caracteres se interpretan como saltos de línea:  
  
-   CRLF: Retorno de carro \+ salto de línea, caracteres Unicode 000D \+ 000A  
  
-   LF: Salto de línea, carácter Unicode 000A  
  
-   NEL: Línea siguiente, carácter Unicode 0085  
  
-   LS: Separador de líneas, carácter Unicode 2028  
  
-   PS: Separador de párrafos, carácter Unicode 2029  
  
 Texto que se copia desde otras aplicaciones mantiene la codificación original y el carácter de salto de línea.  Por ejemplo, al copiar texto desde el Bloc de notas y péguelo en un archivo de texto en Visual Studio, el texto tiene la misma configuración que tenía en el Bloc de notas.  
  
 Al abrir un archivo que tiene un carácter de salto de línea diferente, verá un cuadro de diálogo que pregunta si se deben normalizar los caracteres de salto de línea incoherentes y qué tipo de saltos de línea para elegir.