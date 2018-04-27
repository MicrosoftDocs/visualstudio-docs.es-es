---
title: Usar conjuntos de reglas para especificar las reglas C++ que se van a ejecutar
ms.date: 04/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: ccb64fba6a646de0974c9de6e35beb98738b7300
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2018
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>Usar conjuntos de reglas para especificar las reglas de C++ en ejecución

En Visual Studio, puede crear y modificar un personalizado *conjunto de reglas* para satisfacer las necesidades concretas del proyecto asociadas al análisis de código. Los conjuntos de reglas predeterminados se almacenan en `%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`.

**Visual Studio 2017 versión 15,7** puede crear conjuntos de reglas personalizadas con cualquier texto editor y aplicarlas en las compilaciones de línea de comandos con independencia de lo que utilizas de sistema de compilación. Para obtener más información, consulte [/ analyze: conjunto de reglas](/cpp/build/reference/analyze-code-quality).

Para crear una regla personalizada de C++ en Visual Studio, un proyecto de C o C++ debe estar abierto en el IDE de Visual Studio. Y, a continuación, abra un conjunto de reglas estándar en el editor de conjunto de reglas, a continuación, agregar o quitar reglas concretas y, opcionalmente, cambiar la acción que se produce cuando el análisis de código determina que se ha infringido una regla.

Para crear un nuevo conjunto de reglas personalizado, guárdelo con un nuevo nombre de archivo. El conjunto de reglas personalizado se asigna automáticamente al proyecto.

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Para crear una regla personalizada a partir de un solo conjunto de reglas existente

1. En el Explorador de soluciones, abra el menú contextual para el proyecto y, a continuación, elija **propiedades**.

2. En el **propiedades** ficha, elija **análisis de código**.

3. En el **conjunto de reglas** lista desplegable, realice una de las siguientes acciones:

    - Elija el conjunto de reglas que desea personalizar.

     \- o -

    - Elija  **\<Examinar... >** para especificar el conjunto de una regla existente que no esté en la lista.

4. Elija **abiertos** para mostrar las reglas en el editor de conjunto de reglas.

## <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Para modificar un conjunto de reglas en el editor de conjuntos de reglas

- Para cambiar el nombre para mostrar del conjunto de reglas, en la **vista** menú, elija **ventana propiedades**. Escriba el nombre para mostrar en el **nombre** cuadro. Observe que el nombre para mostrar puede diferir del nombre de archivo.

- Para agregar todas las reglas del grupo a un conjunto de reglas personalizado, active la casilla del grupo. Para quitar todas las reglas del grupo, desactive la casilla.

- Para agregar una regla concreta al conjunto de reglas personalizado, active la casilla de la regla. Para quitar la regla del conjunto de reglas, desactive la casilla.

- Para cambiar la acción realizada cuando se infringe una regla en un análisis de código, elija la **acción** por la regla de campo y, a continuación, elija uno de los siguientes valores:

     **Advertir** -genera una advertencia.

     **Error** -genera un error.

     **Ninguno** -deshabilita la regla. Esta acción es igual que quitar la regla del conjunto de reglas.

## <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Para agrupar, filtrar o cambiar los campos del editor de conjuntos de reglas mediante la barra de herramientas del editor

- Para expandir las reglas de todos los grupos, elija **Expandir todo**.

- Para contraer las reglas en todos los grupos, elija **Contraer todo**.

- Para cambiar el campo que las reglas se agrupan por, elija el campo de la **Group By** lista. Para mostrar las reglas desagrupadas, seleccione  **\<ninguno >**.

- Para agregar o quitar campos en las columnas de la regla, elija **opciones de columna**.

- Para ocultar reglas que no se aplican a la solución actual, elija **ocultar reglas que no se aplican a la solución actual**.

- Para alternar entre mostrar y ocultar reglas que tienen asignadas la acción Error, elija **Mostrar reglas que pueden generar errores de análisis de código**.

- Para alternar entre mostrar y ocultar reglas que tienen asignadas la acción advertencia, elija **Mostrar reglas que pueden generar advertencias de análisis de código**.

- Para alternar entre mostrar y ocultar reglas que tienen asignada la **ninguno** acción, elija **Mostrar reglas que no estén habilitadas**.

- Para agregar o quitar conjuntos de reglas predeterminados para el conjunto de reglas actual de Microsoft, elija **agregar o quitar conjuntos de reglas secundarios**.

## <a name="to-create-a-rule-set-in-a-text-editor"></a>Para crear un conjunto de reglas en un editor de texto

Puede crear un conjunto de reglas personalizado en el texto del editor, almacenar en cualquier ubicación con un `.ruleset` extensión y se aplican en con el [/ analyze: conjunto de reglas](/cpp/build/reference/analyze-code-quality) opción del compilador.

En el ejemplo siguiente se muestra que una regla básica establece el archivo que puede usar como punto de partida:

```xml

<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```
