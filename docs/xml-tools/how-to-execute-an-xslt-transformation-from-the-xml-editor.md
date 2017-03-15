---
title: "C&#243;mo: Ejecutar una transformaci&#243;n XSLT desde el Editor XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# C&#243;mo: Ejecutar una transformaci&#243;n XSLT desde el Editor XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El Editor XML permite asociar una hoja de estilos XSLT con un documento XML, realizar la transformación y ver el resultado.El resultado de la transformación XSLT se muestra en una nueva ventana de documento.  
  
 La propiedad **Resultados** especifica el nombre de archivo del resultado.Si esta propiedad **Resultados** está en blanco, se genera un nombre de archivo en el directorio temporal.La extensión de archivo se basa en el elemento `xsl:output` de la hoja de estilos y puede ser .xml, .txt o .htm.  
  
 Si la propiedad **Resultados** especifica un nombre de archivo con una extensión .htm o .html, se puede obtener una vista previa del resultado XSLT mediante [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Internet Explorer.Todas las demás extensiones de archivo se abren con el editor predeterminado que elija [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio.Por ejemplo, si la extensión de archivo es .xml, Visual Studio utiliza el Editor XML.  
  
### Para ejecutar una transformación XSLT desde un documento XML  
  
1.  Abra un documento XML en el Editor XML.  
  
2.  Asocie una hoja de estilos XSLT con el documento XML.  
  
    -   Agregue una instrucción de procesamiento `xml-stylesheet` al documento XML.Por ejemplo, agregue la siguiente línea `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` al prólogo del documento.  
  
         \-o\-  
  
    -   Agregue la hoja de estilos XSLT mediante la ventana **Propiedades**.En la ventana **Propiedades** del documento, haga clic en el botón **Examinar** del campo **Hoja de estilos**, seleccione la hoja de estilos XSLT y haga clic en **Abrir**.  
  
3.  Haga clic en el botón **Mostrarresultado XSL** de la barra de herramientas del **Editor XML**.  
  
    > [!NOTE]
    >  Si no hay ninguna hoja de estilos asociada con el documento XML, un cuadro de diálogo le pide que proporcione la hoja de estilos que desea utilizar.  
    >   
    >  El resultado de la transformación XSLT se muestra en una nueva ventana de documento.  
  
### Para ejecutar una transformación XSLT desde una hoja de estilos XSLT  
  
1.  Abra una hoja de estilos XSLT en el Editor XML.  
  
2.  Especifique un documento XML en el campo **Entrada** de la ventana **Propiedades** del documento.  
  
    > [!NOTE]
    >  El documento XML es el documento de entrada que se utiliza en la transformación.Si no se especifica un documento cuando se inicia la transformación XSLT, aparece el cuadro de diálogo **Abrir archivo** y podrá especificar un documento en ese momento.  
  
3.  Haga clic en el botón **Mostrarresultado XSLT** de la barra de herramientas del **Editor XML**.  
  
     El resultado de la transformación XSLT se muestra en una nueva ventana de documento.  
  
### Para proporcionar un nombre de archivo de salida diferente  
  
1.  Especifique un nombre de archivo en el campo **Resultados** de la ventana **Propiedades** del documento.  
  
2.  Haga clic en el botón **Mostrarresultado XSLT** de la barra de herramientas del **Editor XML**.  
  
     El resultado de la transformación XSLT se muestra en una nueva ventana de documento y el editor que se utilice en la ventana de salida dependerá de la extensión de archivo de la propiedad del documento **Resultados**.  
  
## Vea también  
 [Editor XML](../xml-tools/xml-editor.md)