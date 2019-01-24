---
title: Usar el Editor de conjunto de reglas de análisis de código
ms.date: 04/04/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 548f50b3d348c520ed7746b7dc3d123ffeb4c6aa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826041"
---
# <a name="use-the-code-analysis-rule-set-editor"></a>Usar el editor de conjunto de reglas de análisis de código

La regla de análisis de código establece el editor le permite que especificar las reglas que se incluyen en una regla personalizada, establezca y la gravedad de las infracciones de reglas.

La siguiente tabla muestra las opciones de gravedad:

|Acción (gravedad)|Descripción|
|-|-|
|Advertencia|Genera una advertencia en el **lista de errores** y también en tiempo de compilación.|
|Error|Genera un error en la **lista de errores** y también en tiempo de compilación.|
|Info|Genera un mensaje en el **lista de errores**.|
|Hidden|La infracción no es visible para el usuario. El IDE se notifica la infracción, sin embargo.|
|Ninguna|Se suprime la regla. El comportamiento es el mismo que si se ha quitado la regla del conjunto de reglas.|

El editor muestra las reglas en una estructura de árbol que agrupa las reglas por una regla de establece el campo especificado. Para agregar o quitar las reglas de un conjunto de reglas, realice uno o varios de los pasos siguientes:

- Active o desactive la casilla de verificación del nodo de grupo para agregar o quitar todas las reglas del grupo. Cuando se selecciona un grupo, todas las reglas se establecen en el **advertencia** acción.

   > [!TIP]
   > Puede cambiar cómo se agrupan las reglas en el **Agrupar por** lista desplegable.

- Haga clic en el **acción** campo de un grupo y, a continuación, especifique la acción que se aplican a todas las reglas del grupo.

- Active o desactive la casilla de verificación de una regla individual. Cuando se selecciona la casilla de verificación para una regla, la regla se establece en la acción de advertencia.

## <a name="toolbar"></a>Barra de herramientas

Puede usar la barra de herramientas del editor de conjunto de reglas para agrupar, filtrar y buscar los datos que aparecen en la cuadrícula de conjunto de reglas.

En la tabla siguiente describe los controles de la barra de herramientas del editor de conjunto de reglas.

|ToolBar (control)|Descripción|
|---------------------|-----------------|
|**Expandir todo**|Muestra las reglas en todos los grupos.|
|**Contraer todo**|Oculta las reglas en todos los grupos.|
|**Group By**|Especifica el campo por el que las reglas se agrupan. Haga clic en  **\<None >** para mostrar las reglas sin grupos.|
|**Opciones de columna**|Especifica los campos de la regla para mostrar.|
|**Ocultar reglas que no se aplican a la solución actual**|Muestra u oculta las reglas que no son del mismo tipo de destino que la solución.|
|**Mostrar reglas que pueden generar errores de análisis de código**|Muestra u oculta las reglas que tienen asignada la acción de Error.|
|**Mostrar reglas que pueden generar advertencias de análisis de código**|Muestra u oculta las reglas que tienen asignadas la acción de advertencia.|
|**Mostrar reglas que no están habilitadas**|Muestra u oculta las reglas que tienen asignada ninguna acción.|
|**Agregar o quitar conjuntos de reglas secundarios**|Agrega o quita las reglas de los conjuntos de reglas seleccionado.|
|**Buscar reglas**|Busca todos los valores de campo de la cadena que especifique.|

## <a name="rule-set-fields"></a>Campos de conjunto de reglas

Campos del conjunto de reglas muestran información sobre un conjunto de reglas y pueden utilizarse para ordenar y agrupar la lista de reglas. Para mostrar u ocultar campos, seleccione **opciones de columna** en la regla establecer la barra de herramientas del editor y, a continuación, active o desactive las casillas de verificación de los campos para mostrar u ocultar.

En la tabla siguiente se describe los campos de un conjunto de reglas:

|Campo|Descripción|
|-----------|-----------------|
|**ID**|El identificador de la regla.|
|**Categoría**|Además de su pertenencia a conjuntos de reglas, reglas de análisis de código también se agrupan por categoría. Para obtener más información, consulte [las advertencias de análisis de código](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Name**|El título de la regla.|
|**Espacio de nombres**|El espacio de nombres de la regla.|
|**Tipo de destino**|Indica si la regla es para nativo, administrado o código base de datos.|
|**Acción**|La acción realizada cuando se infringe la regla en una ejecución de análisis de código. Puede editar el **acción** campo.|
|**Conjuntos de reglas de origen**|El conjunto de reglas que contiene la regla.|

## <a name="sort-and-filter-rule-sets"></a>Ordenar y filtrar conjuntos de reglas

Desde los encabezados de columna de la cuadrícula de conjunto de reglas, puede ordenar y filtrar las reglas por los valores del campo.

- Para ordenar las listas de conjunto de reglas, haga clic en el encabezado de columna del campo por el que desea ordenar. Si los conjuntos de reglas se agrupan, cada grupo se ordena por separado.

- Para filtrar los conjuntos de reglas por el valor de un campo, haga clic en el botón de filtro en el encabezado de columna del campo por el que desea filtrar. Active las casillas de los valores que desea mostrar y desactive las casillas de los valores que desea ocultar.

## <a name="see-also"></a>Vea también

- [Crear un conjunto de reglas personalizado](../code-quality/how-to-create-a-custom-rule-set.md)