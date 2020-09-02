---
title: Errores de FxCopCmd | Microsoft Docs
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
ms.openlocfilehash: 3e0770654f564c57cf576666dcd9575f47d9ce1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787278"
---
# <a name="fxcopcmd-errors"></a>FxCopCmd (errores)
FxCopCmd no considera que todos los errores sean graves. Si FxCopCmd tiene información suficiente para realizar un análisis parcial, realiza el análisis y notifica los errores que se produjeron. El código de error, que es un entero de 32 bits, contiene una combinación bit a bit de valores numéricos que se corresponden con errores.  
  
 En la tabla siguiente se describen los códigos de error devueltos por FxCopCmd:  
  
|Error|Valor numérico|  
|-----------|-------------------|  
|Sin errores|0x0|  
|Error de análisis|0x1|  
|Excepciones de reglas|0x2|  
|Error de carga del proyecto|0x4|  
|Error de carga de ensamblado|0x8|  
|Error de carga de la biblioteca de reglas|0x10|  
|Importar error de carga de informe|0x20|  
|Error de salida|0x40|  
|Error del modificador de la línea de comandos|0x80|  
|Error de inicialización|0x100|  
|Error de referencias de ensamblado|0x200|  
|BuildBreakingMessage|0x400|  
|Error desconocido|0x1000000|  
  
 Se devuelve el error de análisis de errores irrecuperables. Indica que no se pudo completar el análisis. Cuando proceda, el código de error también contiene la causa subyacente del error irrecuperable. Las siguientes condiciones generan errores irrecuperables:  
  
- No se pudo realizar el análisis debido a una entrada insuficiente.  
  
- El análisis produjo una excepción que no está controlada por FxCopCmd.  
  
- No se encontró el archivo de proyecto especificado o está dañado.  
  
- No se especificó la opción output o no se pudo escribir en el archivo.  
  
    > [!NOTE]
    > El código de retorno de FxCopCmd "error de referencias de ensamblado" 0x200 por sí solo es una advertencia en lugar de un error. Este código de retorno indica que se encontraron referencias indirectas que faltan, pero que FxCopCmd pudo controlarlas. Es una advertencia que existe la posibilidad de que algunos resultados del análisis puedan estar en peligro. Considere la posibilidad de que el código de error de referencia de ensamblado se devuelva como un error cuando se combina con cualquier otro código de retorno.  
  
## <a name="see-also"></a>Consulte también  
 [Errores de la aplicación de análisis de código](../code-quality/code-analysis-application-errors.md)