---
title: 'Cómo: crear un conjunto de reglas personalizado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6e4aef02a2bb320112d7d268da28cf66b1ec6751
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657445"
---
# <a name="how-to-create-a-custom-rule-set"></a>Cómo: Crear un conjunto de reglas personalizadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)], [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] y [!INCLUDE[vsPro](../includes/vspro-md.md)], puede crear y modificar un *conjunto de reglas* personalizado para satisfacer las necesidades específicas del proyecto asociadas con el análisis de código. Para crear un conjunto de reglas personalizado, se abren uno o más conjuntos de reglas estándar en el editor del conjuntos de reglas. Se pueden agregar o quitar reglas concretas y cambiar la acción que se realiza cuando el análisis de código determina que se ha infringido una regla.

 Para crear un nuevo conjunto de reglas personalizado, guárdelo con un nuevo nombre de archivo. El conjunto de reglas personalizado se asigna automáticamente al proyecto.

## <a name="opening-the-rule-set-editor"></a>Abrir el editor de conjuntos de reglas

#### <a name="to-open-an-empty-rule-set-file-in-the-rule-set-editor"></a>Para abrir un archivo de conjunto de reglas vacío en el editor de conjuntos de reglas

1. En el menú **archivo** de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], seleccione **nuevo** y haga clic en **archivo**.

2. En el cuadro de diálogo **nuevo archivo** , haga clic en **General** en la lista **plantillas instaladas** y, a continuación, seleccione **conjunto de reglas de análisis de código**.

3. Se abre el editor de conjuntos de reglas. No hay ninguna regla seleccionada en la lista del editor.

#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Para crear una regla personalizada a partir de un solo conjunto de reglas existente

1. En Explorador de soluciones, haga clic con el botón secundario en el proyecto y seleccione **propiedades**.

2. En la pestaña **propiedades** , haga clic en **análisis de código**.

3. En la lista desplegable **conjunto de reglas** , realice una de las acciones siguientes:

   - Seleccione el conjunto de reglas que desee personalizar.

     \- o -

   - Seleccionar **\<Browse... >** para especificar un conjunto de reglas existente que no está en la lista.

4. Haga clic en **abrir** para mostrar las reglas en el editor de conjuntos de reglas.

#### <a name="to-create-a-custom-rule-set-from-multiple-existing-rule-sets"></a>Para crear un conjunto de reglas personalizado a partir de varios conjuntos de reglas existentes

1. En Explorador de soluciones, haga clic con el botón secundario en el proyecto y seleccione **propiedades**.

2. En la pestaña **propiedades** , haga clic en **análisis de código**.

3. Seleccionar **\<Choose varios conjuntos de reglas... >** de **ejecutar este conjunto de reglas**.

4. En el cuadro de diálogo **Agregar o quitar conjuntos de reglas** , seleccione los conjuntos de reglas en los que desea basar el nuevo conjunto de reglas y, a continuación, haga clic en **Aceptar**.

5. Guarde el nuevo conjunto de reglas.

     El nombre del nuevo conjunto de reglas se selecciona en la lista **ejecutar este conjunto de reglas** . Puede cambiar el nombre para mostrar del conjunto de reglas en el paso siguiente.

6. Opta Para cambiar el nombre para mostrar del conjunto de reglas, en el menú **Ver** , haga clic en **ventana Propiedades**. Escriba el nombre para mostrar en el cuadro **nombre** .

7. Para agregar, quitar o modificar reglas de análisis de código específicas en el nuevo conjunto de reglas, haga clic en **abrir**.

## <a name="modifying-a-rule-set"></a>Modificar un conjunto de reglas

#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Para modificar un conjunto de reglas en el editor de conjuntos de reglas

- Para cambiar el nombre para mostrar del conjunto de reglas, en el menú **Ver** , haga clic en **ventana Propiedades**. Escriba el nombre para mostrar en el cuadro **nombre** . Observe que el nombre para mostrar puede diferir del nombre de archivo.

- Para agregar todas las reglas del grupo a un conjunto de reglas personalizado, active la casilla del grupo. Para quitar todas las reglas del grupo, desactive la casilla.

- Para agregar una regla concreta al conjunto de reglas personalizado, active la casilla de la regla. Para quitar la regla del conjunto de reglas, desactive la casilla.

- Para cambiar la acción realizada cuando se infringe una regla en un análisis de código, haga clic en el campo **acción** de la regla y, a continuación, seleccione uno de los siguientes valores:

     **WARN** : genera una advertencia.

     **Error** : genera un error.

     **Ninguno** : deshabilita la regla. Esta acción es igual que quitar la regla del conjunto de reglas.

## <a name="changing-the-rule-set-editor-display"></a>Cambiar la presentación del editor de conjuntos de reglas

#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Para agrupar, filtrar o cambiar los campos del editor de conjuntos de reglas mediante la barra de herramientas del editor

- Para expandir las reglas de todos los grupos, haga clic en **expandir todo**.

- Para contraer las reglas de todos los grupos, haga clic en **contraer todo**.

- Para cambiar el campo por el que se agrupan las reglas, seleccione el campo en la lista **Agrupar por** . Para mostrar las reglas no agrupadas, seleccione **\<None >** .

- Para agregar o quitar campos en columnas de regla, haga clic en **Opciones de columna**.

- Para ocultar reglas que no se aplican a la solución actual, **oculte las reglas que no se aplican a la solución actual**.

- Para cambiar entre mostrar y ocultar reglas que tienen asignada la acción error, haga clic en **Mostrar reglas que pueden generar errores de análisis de código**.

- Para cambiar entre mostrar y ocultar las reglas a las que se asigna la acción ADVERTENCIA, haga clic en **Mostrar reglas que pueden generar advertencias de análisis de código**.

- Para cambiar entre mostrar y ocultar reglas que tienen asignada la acción **ninguno** , haga clic en **Mostrar reglas que no están habilitadas**.

- Para agregar o quitar conjuntos de reglas predeterminadas de Microsoft en el conjunto de reglas actual, haga clic en **Agregar o quitar conjuntos de reglas secundarios**.

## <a name="see-also"></a>Vea también
 [Cómo: configurar el análisis de código para un proyecto de código administrado referencia del conjunto de reglas de análisis de](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md) [código](../code-quality/code-analysis-rule-set-reference.md)
