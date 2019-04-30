---
title: FxCopCmd (errores)
ms.date: 10/19/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.author: gewarren
author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a40d4b7baa3d994ca41213a100881e5f509a5167
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816493"
---
# <a name="fxcopcmd-tool-errors"></a>Errores de la herramienta de FxCopCmd

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

**Error de análisis** se devuelve para los errores irrecuperables. Indica que no se pudo completar el análisis. Cuando sea aplicable, el código de error también contiene la causa subyacente del error irrecuperable. Las condiciones siguientes generan errores irrecuperables:

- No se pudo realizar el análisis debido a una entrada insuficiente.

- El análisis produjo una excepción no controlada por FxCopCmd.

- El archivo de proyecto especificado no se encontró o está dañado.

- No se especificó la opción de salida o no se pudo escribir el archivo.

> [!NOTE]
> Código de retorno de la FxCopCmd **ensamblado hace referencia al error** 0 x 200 por sí misma es una advertencia en lugar de un error. Este código de retorno indica que faltan referencias indirectas, pero que FxCopCmd fue capaz de controlarlos. La advertencia significa que es posible que algunos resultados del análisis podrían haberse visto comprometidos. Tratar **ensamblado hace referencia al error** como un error cuando se combina con cualquier otro código de retorno.

## <a name="see-also"></a>Vea también

- [Errores de la aplicación de análisis de código](../code-quality/code-analysis-application-errors.md)