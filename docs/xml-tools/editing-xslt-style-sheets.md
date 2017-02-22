---
title: "Editar hojas de estilos XSLT | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Editar hojas de estilos XSLT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El Editor XML se puede utilizar también para editar hojas de estilos XSLT.Puede aprovechar las características predeterminadas del editor como IntelliSense, esquematización, fragmentos XML, etc.Además, se incluyen también nuevas características que facilitan la programación en XSLT.  
  
## Características XSLT  
 En la siguiente tabla se describen características específicas del trabajo con hojas de estilos XSLT.  
  
 **Seleccionar el color de la sintaxis**  
 Las palabras clave XSLT, como `template`, `match`, etc., se muestran en el color de palabra clave XSLT especificado en la opción **Fuentes y colores**.  
  
 **Subrayado ondulado**  
 El Editor XML utiliza el archivo xslt.xsd instalado para validar las hojas de estilos XSLT.Los errores de validación se muestran con un subrayado ondulado de color azul.El Editor XML también compila la hoja de estilos en segundo plano e informa de los errores o advertencias del compilador mediante el subrayado ondulado adecuado.  
  
 **Compatibilidad con bloques de scripts**  
 El depurador de XSLT admite el código en bloques de scripts, de modo que puede definir puntos de interrupción y examinar el código del bloque de script.  
  
 **Ver el resultado XSLT**  
 Puede ejecutar una transformación XSL y ver el resultado desde el Editor XML.Para obtener más información, vea [Cómo: Ejecutar una transformación XSLT desde el Editor XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).  
  
 **Depurar XSLT**  
 Puede iniciar el depurador de XSLT desde un archivo XSLT del Editor XML.El depurador admite la definición de puntos de interrupción en el archivo XSLT, la visualización del estado de ejecución de XSLT, etc.Al mantener el mouse sobre una variable XSLT se muestra un cuadro de información sobre herramientas con el valor de la variable.El depurador se puede utilizar para depurar una hoja de estilos o para depurar una transformación XSL compilada invocada desde otra aplicación.Para obtener más información, vea [Depuración de XSLT](../xml-tools/debugging-xslt.md).  
  
## Vea también  
 [Editor XML](../xml-tools/xml-editor.md)