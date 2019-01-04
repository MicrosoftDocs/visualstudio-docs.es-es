---
title: FxCopCmd (errores)
ms.date: 10/19/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: gewarren
author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 34ec1b04e10b874d6f8373b5eb0e6c2e5c6d70e4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53844085"
---
# <a name="fxcopcmd-tool-errors"></a>Errores de la herramienta de FxCopCmd

FxCopCmd no tiene en cuenta todos los errores sea grave. Si FxCopCmd tiene suficiente información para realizar un análisis parcial, realiza los errores de análisis e informes que se ha producido. El código de error, que es un entero de 32 bits, contiene una combinación bit a bit de valores numéricos que se corresponden con errores.

En la tabla siguiente se describe los códigos de error devueltos por FxCopCmd:

|Error|Valor numérico|
|-----------|-------------------|
|Sin errores|0x0|
|Error de análisis|0x1|
|Excepciones de reglas|0 x 2|
|Error al cargar proyecto|0x4|
|Error al cargar ensamblado|0x8|
|Error de carga de biblioteca de regla|0 x 10|
|Error de carga del informe de importación|0 x 20|
|Error de salida|0x40|
|Error del conmutador de línea de comandos|0x80|
|Error de inicialización|0 x 100|
|Error de las referencias de ensamblado|0 x 200|
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