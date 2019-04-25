---
title: FxCopCmd Errors | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: 12
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 016f22591deb019718c8271cf0b307d3f4c597c1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60043113"
---
# <a name="fxcopcmd-errors"></a>FxCopCmd (errores)
FxCopCmd no tiene en cuenta todos los errores sea grave. Si FxCopCmd tiene suficiente información para realizar un análisis parcial, realiza los errores de análisis e informes que se ha producido. El código de error, que es un entero de 32 bits, contiene una combinación bit a bit de valores numéricos que se corresponden con errores.  
  
 En la tabla siguiente se describe los códigos de error devueltos por FxCopCmd:  
  
|Error|Valor numérico|  
|-----------|-------------------|  
|Sin errores|0x0|  
|Error de análisis|0x1|  
|Excepciones de reglas|0x2|  
|Error al cargar proyecto|0x4|  
|Error al cargar ensamblado|0x8|  
|Error de carga de biblioteca de regla|0x10|  
|Error de carga del informe de importación|0x20|  
|Error de salida|0x40|  
|Error del conmutador de línea de comandos|0x80|  
|Error de inicialización|0x100|  
|Error de las referencias de ensamblado|0x200|  
|BuildBreakingMessage|0x400|  
|Error desconocido|0x1000000|  
  
 Se devuelve el error de análisis de errores irrecuperables. Indica que no se pudo completar el análisis. Cuando sea aplicable, el código de error también contiene la causa subyacente del error irrecuperable. Las condiciones siguientes generan errores irrecuperables:  
  
- No se puede realizar el análisis provocado por una entrada insuficiente.  
  
- El análisis produjo una excepción no controlada por FxCopCmd.  
  
- El archivo de proyecto especificado no se encontró o está dañado.  
  
- No se especificó la opción de salida o no se pudo escribir el archivo.  
  
    > [!NOTE]
    >  El FxCopCmd código de retorno "Error de referencias de ensamblado" 0 x 200 por sí misma es una advertencia en lugar de un error. Este código de retorno indica que se encontraron referencias indirectas que faltan pero que FxCopCmd fue posible controlarlos. Es una advertencia que hay una posibilidad de que algunos resultados del análisis podrían haberse visto comprometidos. Considere la posibilidad de código de retorno "Error de referencias de ensamblado" como un error cuando se combina con cualquier otro código de retorno.  
  
## <a name="see-also"></a>Vea también  
 [Errores de la aplicación de análisis de código](../code-quality/code-analysis-application-errors.md)