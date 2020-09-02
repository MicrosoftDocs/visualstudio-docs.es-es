---
title: Usar el editor de conjuntos de reglas de análisis de código
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1e53df97c0535f59d0b96e9608ad55f2cb5ab21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "88893312"
---
# <a name="use-the-code-analysis-rule-set-editor"></a>Usar el editor de conjuntos de reglas de análisis de código

El editor de conjuntos de reglas de análisis de código le permite especificar las reglas que se incluyen en un conjunto de reglas personalizado y establecer la gravedad de las infracciones de las reglas.

En la tabla siguiente se muestran las opciones de gravedad:

|Acción (gravedad)|Descripción|
|-|-|
|Advertencia|Genera una advertencia en el **lista de errores** y también en el momento de la compilación.|
|Error|Genera un error en el **lista de errores** y también en el momento de la compilación.|
|Información|Genera un mensaje en el **lista de errores**.|
|Hidden|La infracción no es visible para el usuario. No obstante, el IDE recibe una notificación de la infracción.|
|Ninguno|Se suprime la regla. El comportamiento es el mismo que si se quitara la regla del conjunto de reglas.|

El editor muestra las reglas en una estructura de árbol que agrupa las reglas por un campo de conjunto de reglas que especifique. Para agregar o quitar reglas de un conjunto de reglas, realice uno o varios de los pasos siguientes:

- Active o desactive la casilla del nodo grupo para agregar o quitar todas las reglas del grupo. Al seleccionar un grupo, todas las reglas se establecen en la acción **ADVERTENCIA** .

   > [!TIP]
   > Puede cambiar la forma en que se agrupan las reglas en la lista desplegable **Agrupar por** .

- Haga clic en el campo **acción** de un grupo y especifique la acción que se aplicará a todas las reglas del grupo.

- Active o desactive la casilla de una regla individual. Al activar la casilla de una regla, la regla se establece en la acción **ADVERTENCIA** .

## <a name="toolbar"></a>Barra de herramientas

Puede usar la barra de herramientas del editor de conjuntos de reglas para agrupar, filtrar y buscar los datos que aparecen en la cuadrícula del conjunto de reglas.

En la tabla siguiente se describen los controles de la barra de herramientas del editor de conjuntos de reglas.

|Toolbar (control)|Descripción|
|---------------------|-----------------|
|**Expandir todo**|Muestra las reglas de todos los grupos.|
|**Contraer todo**|Oculta las reglas de todos los grupos.|
|**Agrupar por**|Especifica el campo por el que se agrupan las reglas. Haga clic **\<None>** para mostrar las reglas sin grupos.|
|**Opciones de Column**|Especifica los campos de regla que se van a mostrar.|
|**Ocultar reglas que no se aplican a la solución actual**|Muestra u oculta reglas que no son del mismo tipo de destino que la solución.|
|**Mostrar reglas que pueden generar errores de análisis de código**|Muestra u oculta las reglas a las que se ha asignado la acción de error.|
|**Mostrar reglas que pueden generar advertencias de análisis de código**|Muestra u oculta las reglas a las que se ha asignado la acción de advertencia.|
|**Mostrar reglas que no están habilitadas**|Muestra u oculta las reglas a las que se ha asignado la acción none.|
|**Agregar o quitar conjuntos de reglas secundarios**|Agrega o quita las reglas de los conjuntos de reglas seleccionados.|
|**Reglas de búsqueda**|Busca en todos los valores de campo la cadena que especifique.|

## <a name="rule-set-fields"></a>Campos de conjunto de reglas

Los campos de conjunto de reglas muestran información sobre un conjunto de reglas y se pueden usar para ordenar y agrupar la lista de reglas. Para mostrar u ocultar campos, seleccione **Opciones de columna** en la barra de herramientas del editor de conjuntos de reglas y, a continuación, Active o desactive las casillas de los campos que desea mostrar u ocultar.

En la tabla siguiente se describen los campos de un conjunto de reglas:

|Campo|Descripción|
|-----------|-----------------|
|**Id**|El identificador de la regla.|
|**Categoría**|Además de su pertenencia en conjuntos de reglas, las reglas de análisis de código también se agrupan por categoría. Para obtener más información, vea [advertencias de análisis de código](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Name**|Título de la regla.|
|**Espacio de nombres**|Espacio de nombres de la regla.|
|**Tipo de destino**|Indica si la regla es para el código nativo, administrado o de base de datos.|
|**Acción**|Acción que se realiza cuando se infringe la regla en una ejecución de análisis de código. Puede editar el campo de **acción** .|
|**Conjuntos de reglas de origen**|Conjunto de reglas que contiene la regla.|

## <a name="sort-and-filter-rule-sets"></a>Ordenar y filtrar conjuntos de reglas

En los encabezados de columna de la cuadrícula del conjunto de reglas, puede ordenar y filtrar las reglas por los valores del campo.

- Para ordenar las listas de conjuntos de reglas, seleccione el encabezado de columna del campo por el que desea ordenar. Si los conjuntos de reglas están agrupados, cada grupo se ordena individualmente.

- Para filtrar los conjuntos de reglas por el valor de un campo, seleccione el botón de filtro en el encabezado de columna del campo por el que desea filtrar. Active las casillas de los valores que desea mostrar y desactive las casillas de los valores que desea ocultar.

## <a name="see-also"></a>Consulte también

- [Creación de un conjunto de reglas personalizadas](../code-quality/how-to-create-a-custom-rule-set.md)
