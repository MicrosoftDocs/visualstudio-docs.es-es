---
title: FxCopCmd (errores) | Documentos de Microsoft
ms.custom: 
ms.date: 10/19/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: 
ms.author: gewarren
author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 48b082f5b00f260d2f8e2519a4551fab23dc1011
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="fxcopcmd-errors"></a>FxCopCmd (errores)
FxCopCmd no tiene en cuenta todos los errores como irrecuperable. Si FxCopCmd tiene suficiente información para realizar un análisis parcial, realiza el análisis y notifica los errores que se produjeron. El código de error, que es un entero de 32 bits, contiene una combinación bit a bit de valores numéricos que se corresponden con errores.  
  
 En la tabla siguiente se describe los códigos de error devueltos por FxCopCmd:  
  
|Error|Valor numérico|  
|-----------|-------------------|  
|Sin errores|0 x 0|  
|Error de análisis|0 x 1|  
|Excepciones de reglas|0 x 2|  
|Error de carga del proyecto|0 x 4|  
|Error de carga de ensamblado|0 x 8|  
|Error de carga de biblioteca de regla|0 x 10|  
|Error de carga del informe de importación|0 x 20|  
|Error de salida|0 x 40|  
|Error de modificador de línea de comandos|0 x 80|  
|Error de inicialización|0 x 100|  
|Error de referencias de ensamblado|0 x 200|  
|BuildBreakingMessage|0 x 400|  
|Error desconocido|0 x 1000000|  
  
 Se devuelve el error de análisis de errores irrecuperables. Indica que no se pudo completar el análisis. Cuando sea aplicable, el código de error también contiene la causa subyacente del error irrecuperable. Las condiciones siguientes generan errores irrecuperables:  
  
-   El análisis no se pudo realizar provocado por una entrada insuficiente.  
  
-   El análisis produjo una excepción no controlada por FxCopCmd.  
  
-   El archivo de proyecto especificado no se encuentra o está dañado.  
  
-   No se especificó la opción de salida o no se pudo escribir el archivo.  
  
    > [!NOTE]
    >  El FxCopCmd código de retorno "Error de referencias de ensamblado" 0 x 200 por sí misma es una advertencia en lugar de un error. Este código de retorno indica que se encontraron referencias indirectas que faltan pero que FxCopCmd fue capaz de abordar estos. Es una advertencia que es posible que algunos resultados del análisis podrían haberse visto comprometidos. Considere la posibilidad de código de retorno "Error de referencias de ensamblado" como un error cuando se combina con cualquier otro código de retorno.  
  
## <a name="see-also"></a>Vea también  
 [Errores de la aplicación de análisis de código](../code-quality/code-analysis-application-errors.md)