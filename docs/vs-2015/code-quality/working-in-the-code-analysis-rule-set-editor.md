---
title: Trabajar en el editor de conjuntos de reglas de análisis de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f25cc5a5f56c20f6a1696baa5aa3e9ee5ebdf2fc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72621507"
---
# <a name="working-in-the-code-analysis-rule-set-editor"></a>Trabajar en el editor de conjuntos de reglas de análisis de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El editor de conjuntos de reglas de análisis de código le permite especificar las reglas que se incluyen en un conjunto de reglas personalizado y especificar la acción. También puede especificar la acción que debe llevarse a cabo cuando el análisis de código encuentra una infracción de la regla.

|Acción|Descripción|
|------------|-----------------|
|**Advertencia**|Genera una advertencia en la ventana de **lista de errores** .|
|**Error**|Genera un error en la ventana de **lista de errores** .|
|**Ninguno**|Deshabilita la regla.|

 El editor muestra las reglas en una estructura de árbol que agrupa las reglas por un campo de conjunto de reglas que especifique. Para agregar o quitar reglas de un conjunto de reglas, realice uno o varios de los pasos siguientes:

- Active o desactive la casilla del nodo grupo para agregar o quitar todas las reglas del grupo. Al seleccionar un grupo, todas las reglas se establecen en la acción **ADVERTENCIA** .

- Haga clic en el campo **acción** de un grupo y, a continuación, especifique la acción que se aplicará a todas las reglas del grupo.

- Active o desactive la casilla de una regla individual. Al activar la casilla de una regla, la regla se establece en la acción ADVERTENCIA.

## <a name="rule-set-editor-toolbar"></a>Barra de herramientas del editor de conjuntos de reglas
 Puede usar la barra de herramientas del editor de conjuntos de reglas para agrupar, filtrar y buscar los datos que aparecen en la cuadrícula del conjunto de reglas.

 En la tabla siguiente se describen los controles de la barra de herramientas del editor de conjuntos de reglas.

|Toolbar (control)|Descripción|
|---------------------|-----------------|
|**Expandir todo**|Muestra las reglas de todos los grupos.|
|**Contraer todo**|Oculta las reglas de todos los grupos.|
|**Group By**|Especifica el campo por el que se agrupan las reglas. Haga clic en **\<None >** para mostrar las reglas sin grupos.|
|**Opciones de columna**|Especifica los campos de regla que se van a mostrar.|
|**Ocultar reglas que no se aplican a la solución actual**|Muestra u oculta reglas que no son del mismo tipo de destino que la solución.|
|**Mostrar reglas que pueden generar errores de análisis de código**|Muestra u oculta las reglas a las que se ha asignado la acción de error.|
|**Mostrar reglas que pueden generar advertencias de análisis de código**|Muestra u oculta las reglas a las que se ha asignado la acción de advertencia.|
|**Mostrar reglas que no están habilitadas**|Muestra u oculta las reglas a las que se ha asignado la acción none.|
|**Agregar o quitar conjuntos de reglas secundarios**|Agrega o quita las reglas de los conjuntos de reglas seleccionados.|
|**Reglas de búsqueda**|Busca en todos los valores de campo la cadena que especifique.|

## <a name="rule-set-fields"></a>Campos de conjunto de reglas
 Los campos de conjunto de reglas muestran información sobre un conjunto de reglas y se pueden usar para ordenar y agrupar la lista de reglas. Para mostrar u ocultar campos, haga clic en **Opciones de columna** en la barra de herramientas del editor de conjuntos de reglas y, a continuación, Active o desactive las casillas de los campos que desea mostrar u ocultar.

 En la tabla siguiente se describen los campos de un conjunto de reglas.

|Campo|Descripción|
|-----------|-----------------|
|**ID**|Identificador de la regla.|
|**Categoría**|Además de su pertenencia en conjuntos de reglas, las reglas de análisis de código también se agrupan por categoría. Para obtener más información, vea [análisis de código para advertencias de código administrado](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Nombre**|Título de la regla.|
|**Namespace**|Espacio de nombres de la regla.|
|**Tipo de destino**|Indica si la regla es para el código nativo, administrado o de base de datos.|
|**Acción**|Acción que se realiza cuando se infringe la regla en una ejecución de análisis de código.<br /><br /> **ADVERTENCIA** : genera una advertencia.<br /><br /> **Error** : genera un error.<br /><br /> **Ninguno** : deshabilita la regla.<br /><br /> Puede editar el campo de acción. Establecer el valor en ninguno es lo mismo que desactivar la casilla de la regla.|
|**Conjuntos de reglas de origen**|Conjunto de reglas que contiene la regla.|

## <a name="sorting-and-filtering-rule-sets"></a>Ordenar y filtrar conjuntos de reglas
 En los encabezados de columna de la cuadrícula del conjunto de reglas, puede ordenar y filtrar las reglas por los valores del campo.

- Para ordenar las listas de conjuntos de reglas, haga clic en el encabezado de columna del campo por el que desea ordenar. Si los conjuntos de reglas están agrupados, cada grupo se ordena individualmente.

- Para filtrar los conjuntos de reglas por el valor de un campo, haga clic en el botón filtro del encabezado de columna del campo por el que desea filtrar. Active las casillas de los valores que desea mostrar y desactive las casillas de los valores que desea ocultar.
