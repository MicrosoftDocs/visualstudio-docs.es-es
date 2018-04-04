---
title: FxCopCmd (errores) | Documentos de Microsoft
ms.date: 10/19/2016
ms.technology: vs-ide-code-analysis
ms.topic: article
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: gewarren
author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b407167a772a82b56c39ba222dc3c1f563f5c012
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2018
---
# <a name="fxcopcmd-tool-errors"></a>Errores de la herramienta de FxCopCmd

FxCopCmd no tiene en cuenta todos los errores como irrecuperable. Si FxCopCmd tiene suficiente información para realizar un análisis parcial, realiza el análisis y notifica los errores que se produjeron. El código de error, que es un entero de 32 bits, contiene una combinación bit a bit de valores numéricos que se corresponden con errores.

En la tabla siguiente se describe los códigos de error devueltos por FxCopCmd:

|Error|Valor numérico|
|-----------|-------------------|
|Sin errores|0x0|
|Error de análisis|0x1|
|Excepciones de reglas|0x2|
|Error de carga del proyecto|0x4|
|Error de carga de ensamblado|0x8|
|Error de carga de biblioteca de regla|0x10|
|Error de carga del informe de importación|0x20|
|Error de salida|0x40|
|Error de modificador de línea de comandos|0x80|
|Error de inicialización|0x100|
|Error de referencias de ensamblado|0x200|
|BuildBreakingMessage|0x400|
|Error desconocido|0x1000000|

**Error de análisis** se devuelve para los errores irrecuperables. Indica que no se pudo completar el análisis. Cuando sea aplicable, el código de error también contiene la causa subyacente del error irrecuperable. Las condiciones siguientes generan errores irrecuperables:

- El análisis no se pudo realizar debido a una entrada insuficiente.

- El análisis produjo una excepción no controlada por FxCopCmd.

- El archivo de proyecto especificado no se encuentra o está dañado.

- No se especificó la opción de salida o no se pudo escribir el archivo.

> [!NOTE]
> Código de retorno de la FxCopCmd **ensamblado hace referencia al error** 0 x 200 por sí misma es una advertencia en lugar de un error. Este código de retorno indica que faltan referencias indirectas, pero que FxCopCmd fue capaz de abordar estos. La advertencia significa que es posible que algunos resultados del análisis podrían haberse visto comprometidos. Tratar **ensamblado hace referencia al error** como un error cuando se combina con cualquier otro código de retorno.

## <a name="see-also"></a>Vea también

- [Errores de la aplicación de análisis de código](../code-quality/code-analysis-application-errors.md)