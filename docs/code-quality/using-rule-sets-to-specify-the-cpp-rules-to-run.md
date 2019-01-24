---
title: Usar conjuntos de reglas para especificar las reglas C++ que se van a ejecutar
ms.date: 04/28/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: a556b0bb051ea25b438f91696b5e55b0c984115c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53873540"
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>Usar conjuntos de reglas para especificar las reglas de C++ en ejecución

En Visual Studio, puede crear y modificar una personalizada *conjunto de reglas* para satisfacer las necesidades concretas del proyecto asociadas con el análisis de código. Los conjuntos de reglas predeterminado se almacenan en `%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`.

**Visual Studio 2017 versión 15.7** puede crear conjuntos de reglas personalizadas con cualquier texto editor y aplicarlas en las compilaciones de línea de comandos con independencia de lo que usa el sistema de compilación. Para obtener más información, consulte [/ analyze: ruleset](/cpp/build/reference/analyze-code-analysis).

Para crear una regla personalizada de C++ en Visual Studio, un proyecto de C o C++ debe estar abierto en el IDE de Visual Studio. Y, a continuación, abra un conjunto de reglas estándar en el editor de conjunto de reglas, a continuación, agregar o quitar reglas concretas y, opcionalmente, cambiar la acción que se produce cuando el análisis de código determina que se ha infringido una regla.

Para crear un nuevo conjunto de reglas personalizado, guárdelo con un nuevo nombre de archivo. El conjunto de reglas personalizado se asigna automáticamente al proyecto.

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Para crear una regla personalizada a partir de un solo conjunto de reglas existente

1. En el Explorador de soluciones, abra el menú contextual para el proyecto y, a continuación, elija **propiedades**.

2. En el **propiedades** ficha, elija **análisis de código**.

3. En el **Pravidel** lista desplegable, realice una de las siguientes acciones:

   - Elija el conjunto de reglas que desea personalizar.

     \- o -

   - Elija  **\<Examinar... >** especificar una regla existente conjunto que no está en la lista.

4. Elija **abierto** para mostrar las reglas en el editor de conjunto de reglas.

## <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Para modificar un conjunto de reglas en el editor de conjuntos de reglas

- Para cambiar el nombre para mostrar del conjunto de reglas, en el **vista** menú, elija **ventana propiedades**. Escriba el nombre para mostrar en el **nombre** cuadro. Observe que el nombre para mostrar puede diferir del nombre de archivo.

- Para agregar todas las reglas del grupo a un conjunto de reglas personalizado, active la casilla del grupo. Para quitar todas las reglas del grupo, desactive la casilla.

- Para agregar una regla concreta al conjunto de reglas personalizado, active la casilla de la regla. Para quitar la regla del conjunto de reglas, desactive la casilla.

- Para cambiar la acción realizada cuando se infringe una regla en un análisis de código, elija el **acción** por la regla de campo y, a continuación, elija uno de los valores siguientes:

     **Advertir** -genera una advertencia.

     **Error** -genera un error.

     **Ninguno** -deshabilita la regla. Esta acción es igual que quitar la regla del conjunto de reglas.

## <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Para agrupar, filtrar o cambiar los campos del editor de conjuntos de reglas mediante la barra de herramientas del editor

- Para expandir las reglas en todos los grupos, elija **Expandir todo**.

- Para contraer las reglas en todos los grupos, elija **Contraer todo**.

- Para cambiar el campo que las reglas se agrupan por, elija el campo desde el **Group By** lista. Para mostrar las reglas desagrupadas, seleccione  **\<None >**.

- Para agregar o quitar campos en las columnas de la regla, elija **opciones de columna**.

- Para ocultar reglas que no se aplican a la solución actual, elija **ocultar reglas que no se aplican a la solución actual**.

- Para alternar entre mostrar y ocultar reglas que tienen asignada la acción de Error, elija **Mostrar reglas que pueden generar errores de análisis de código**.

- Para alternar entre mostrar y ocultar reglas que tienen asignadas la acción advertencia, elija **Mostrar reglas que pueden generar advertencias de análisis de código**.

- Para alternar entre mostrar y ocultar reglas que tienen asignada la **ninguno** acción, elija **Mostrar reglas no habilitadas**.

- Para agregar o quitar conjuntos de reglas predeterminados para el conjunto de reglas actual de Microsoft, elija **agregar o quitar conjuntos de reglas secundarios**.

## <a name="to-create-a-rule-set-in-a-text-editor"></a>Para crear un conjunto de reglas en un editor de texto

Puede crear un conjunto de reglas personalizado en el texto del editor, almacénelo en cualquier ubicación con un `.ruleset` extensión y se aplican en con el [/ analyze: ruleset](/cpp/build/reference/analyze-code-analysis) opción del compilador.

El ejemplo siguiente se muestra que una regla básica de establece el archivo que puede usar como punto de partida:

```xml

<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```
