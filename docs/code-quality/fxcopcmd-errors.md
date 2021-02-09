---
title: FxCopCmd (errores)
ms.date: 10/19/2016
description: Obtenga información sobre los códigos de error que devuelve el comando FxCopCmd. Vea qué tipo de error representa cada código y descubra cómo reconocer errores irrecuperables.
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: mikejo
author: mikejo5000
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: efeabd85bbf2753dd3f5e37a43e0918b7f95d7fe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860222"
---
# <a name="fxcopcmd-tool-errors"></a>Errores de la herramienta FxCopCmd

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

Se devuelve un **error de análisis** de errores irrecuperables. Indica que no se pudo completar el análisis. Cuando proceda, el código de error también contiene la causa subyacente del error irrecuperable. Las siguientes condiciones generan errores irrecuperables:

- No se pudo realizar el análisis debido a una entrada insuficiente.

- El análisis produjo una excepción que no está controlada por FxCopCmd.

- No se encontró el archivo de proyecto especificado o está dañado.

- No se especificó la opción output o no se pudo escribir en el archivo.

> [!NOTE]
> El ensamblado del código de retorno de FxCopCmd **hace referencia a error** 0x200 por sí solo es una advertencia en lugar de un error. Este código de retorno indica que faltan referencias indirectas, pero que FxCopCmd pudo controlarlas. La ADVERTENCIA significa que hay una posibilidad de que algunos resultados del análisis puedan estar en peligro. El tratamiento de **las referencias de ensamblado** es un error cuando se combina con cualquier otro código de retorno.

## <a name="see-also"></a>Vea también

- [Errores de la aplicación de análisis de código](../code-quality/code-analysis-application-errors.md)
