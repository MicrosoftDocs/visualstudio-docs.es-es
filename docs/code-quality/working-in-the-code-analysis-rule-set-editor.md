---
title: Usar el Editor de conjunto de reglas de análisis de código en Visual Studio
ms.date: 04/-4/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0791cc3d4dadf132dc2da7ad591eaaca27a3a1dc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="use-the-code-analysis-rule-set-editor"></a>Utilice el editor de conjunto de reglas de análisis de código

El editor de conjunto de reglas de análisis de código permite especificar las reglas que se incluyen en un conjunto de reglas personalizado y la gravedad de las infracciones de reglas.

|Acción (gravedad)|Descripción|
|-|-|
|Advertencia|Genera una advertencia en el **lista de errores** y también en tiempo de compilación.|
|Error|Genera un error en la **lista de errores** y también en tiempo de compilación.|
|Info|Genera un mensaje en el **lista de errores**.|
|Hidden|La infracción no es visible para el usuario. El IDE se notifica la infracción, sin embargo.|
|Ninguna|Se suprime la regla. El comportamiento es el mismo que si se ha quitado la regla del conjunto de reglas.|

El editor muestra las reglas en una estructura de árbol que agrupa las reglas por una regla de establece el campo especificado. Para agregar o quitar reglas de un conjunto de reglas, realice uno o varios de los siguientes pasos:

- Active o desactive la casilla de verificación del nodo de grupo para agregar o quitar todas las reglas del grupo. Cuando se selecciona un grupo, todas las reglas se establecen en los **advertencia** acción.

   > [!TIP]
   > Puede cambiar cómo se agrupan las reglas en la **Agrupar por** lista desplegable.

- Haga clic en el **acción** campo de un grupo y, a continuación, especifique la acción que se va a aplicar a todas las reglas del grupo.

- Active o desactive la casilla de verificación para una de las reglas. Cuando se selecciona la casilla de verificación para una regla, la regla se establece en la acción de advertencia.

## <a name="toolbar"></a>Barra de herramientas

Puede utilizar la barra de herramientas del editor de conjunto de reglas para agrupar, filtrar y buscar los datos que aparecen en la cuadrícula de conjunto de reglas.

En la siguiente tabla describe los controles de la barra de herramientas del editor de conjunto de reglas.

|ToolBar (control)|Descripción|
|---------------------|-----------------|
|**Expandir todo**|Muestra las reglas en todos los grupos.|
|**Contraer todo**|Oculta las reglas en todos los grupos.|
|**Group By**|Especifica el campo por el que se agrupan las reglas. Haga clic en  **\<ninguno >** para mostrar las reglas sin grupos.|
|**Opciones de columna**|Especifica los campos de la regla para mostrar.|
|**Ocultar reglas que no se aplican a la solución actual**|Muestra u oculta las reglas que no son del mismo tipo de destino como la solución.|
|**Mostrar reglas que pueden generar errores de análisis de código**|Muestra u oculta las reglas que tienen asignadas la acción de Error.|
|**Mostrar reglas que pueden generar advertencias de análisis de código**|Muestra u oculta las reglas que tienen asignadas la acción advertencia.|
|**Mostrar reglas que no están habilitadas**|Muestra u oculta las reglas que tienen asignada ninguna acción.|
|**Agregar o quitar conjuntos de reglas secundarios**|Agrega o quita las reglas de los conjuntos de reglas seleccionado.|
|**Reglas de búsqueda**|Busca todos los valores de campo de la cadena que especifique.|

## <a name="rule-set-fields"></a>Campos de conjunto de reglas

Campos de conjunto de reglas muestran información acerca de un conjunto de reglas y pueden utilizarse para ordenar y agrupar la lista de reglas. Para mostrar u ocultar campos, seleccione **opciones de columna** en la regla de la barra de herramientas del editor y, a continuación, active o desactive las casillas de verificación de los campos para mostrar u ocultar.

En la tabla siguiente se describe los campos de un conjunto de reglas:

|Campo|Descripción|
|-----------|-----------------|
|**ID**|El identificador de la regla.|
|**Categoría**|Además de su pertenencia a conjuntos de reglas, reglas de análisis de código también se agrupan por categoría. Para obtener más información, consulte [las advertencias del análisis de código](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Name**|El título de la regla.|
|**Espacio de nombres**|El espacio de nombres de la regla.|
|**Tipo de destino**|Indica si la regla es de nativo, administrado o código base de datos.|
|**Acción**|La acción realizada cuando se infringe la regla en un ejecución del análisis de código. Puede editar la **acción** campo.|
|**Conjuntos de reglas de origen**|El conjunto de reglas que contiene la regla.|

## <a name="sort-and-filter-rule-sets"></a>Ordenar y filtrar conjuntos de reglas

Desde los encabezados de columna de la cuadrícula de conjunto de reglas, puede ordenar y filtrar las reglas por los valores del campo.

- Para ordenar las listas de conjunto de reglas, haga clic en el encabezado de columna del campo por el que desea ordenar. Si los conjuntos de reglas están agrupados, cada grupo se ordena individualmente.

- Para filtrar los conjuntos de reglas por el valor de un campo, haga clic en el botón de filtro en el encabezado de columna del campo por el que desea filtrar. Active las casillas de los valores que desea mostrar y desactive las casillas de verificación de los valores que desea ocultar.

## <a name="see-also"></a>Vea también

- [Crear un conjunto de reglas personalizado](../code-quality/how-to-create-a-custom-rule-set.md)