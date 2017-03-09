---
title: "Errores de FxCopCmd | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FxCopCmd (errores)"
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "susanno"
manager: "douge"
---
# Errores de FxCopCmd
FxCopCmd no considera todos los errores como irrecuperables.  Si FxCopCmd tiene información suficiente para realizar un análisis parcial, realiza el análisis y crea un informe de los errores.  El código de error, que es un entero de 32 bits, contiene una combinación bit a bit de los valores numéricos que corresponden a los errores.  
  
 En la tabla siguiente se describen los códigos de error devueltos por FxCopCmd:  
  
|Error|Valor numérico|  
|-----------|--------------------|  
|Sin errores|0x0|  
|Error de análisis|0x1|  
|Excepciones de reglas|0x2|  
|Error de carga del proyecto|0x4|  
|Error de carga del ensamblado|0x8|  
|Error de carga de la biblioteca de reglas|0x10|  
|Error de carga del informe de importación|0x20|  
|Error de resultados|0x40|  
|Error de modificador de la línea de comandos|0x80|  
|Error de inicialización|0x100|  
|Error de referencias de ensamblado|0x200|  
|BuildBreakingMessage|0x400|  
|Error desconocido|0x1000000|  
  
 El error de análisis se devuelve en caso de errores irrecuperables.  Indica que el análisis no pudo completarse.  Si procede, el código de error también contiene la causa subyacente del error irrecuperable.  Las condiciones siguientes generan errores irrecuperables:  
  
-   El análisis no pudo realizarse debido a una entrada insuficiente.  
  
-   El análisis inició una excepción que FxCopCmd no controla.  
  
-   El archivo de proyecto especificado no se encuentra o está dañado.  
  
-   No se especificó la opción de salida o no se pudo escribir en el archivo.  
  
    > [!NOTE]
    >  El código devuelto por FxCopCmd "Error de referencias de ensamblado" 0x200, más que de un error, se trata de una advertencia.  Este código devuelto indica que se buscaron las referencias indirectas que faltaban, pero que FxCopCmd fue capaz de solucionarlas.  Es una advertencia que indica la posibilidad de que algunos resultados del análisis puedan estar comprometidos.  Considere el código devuelto "Error de referencias de ensamblado" como un error de código cuando aparezca con otro código devuelto.  
  
## Vea también  
 [Errores de la aplicación de análisis de código](../code-quality/code-analysis-application-errors.md)