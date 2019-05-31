---
title: Procedimiento Crear un conjunto de reglas personalizado | Documentos de Microsoft
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 909242aaf8dd4caaee7af75e40554aaff648df68
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045660"
---
# <a name="how-to-create-a-custom-rule-set"></a>Procedimiento Crear un conjunto de reglas personalizadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)], [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)], y [!INCLUDE[vsPro](../includes/vspro-md.md)], puede crear y modificar una personalizada *conjunto de reglas* para satisfacer las necesidades concretas del proyecto asociadas con el análisis de código. Para crear un conjunto de reglas personalizado, se abren uno o más conjuntos de reglas estándar en el editor del conjuntos de reglas. Se pueden agregar o quitar reglas concretas y cambiar la acción que se realiza cuando el análisis de código determina que se ha infringido una regla.  
  
 Para crear un nuevo conjunto de reglas personalizado, guárdelo con un nuevo nombre de archivo. El conjunto de reglas personalizado se asigna automáticamente al proyecto.  
  
## <a name="opening-the-rule-set-editor"></a>Abrir el editor de conjuntos de reglas  
  
#### <a name="to-open-an-empty-rule-set-file-in-the-rule-set-editor"></a>Para abrir un archivo de conjunto de reglas vacío en el editor de conjuntos de reglas  
  
1. En el **archivo** menú de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], apunte a **New** y, a continuación, haga clic en **archivo**.  
  
2. En el **nuevo archivo** cuadro de diálogo, haga clic en **General** en el **plantillas instaladas** lista y, a continuación, seleccione **conjunto de reglas de análisis de código**.  
  
3. Se abre el editor de conjuntos de reglas. No hay ninguna regla seleccionada en la lista del editor.  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Para crear una regla personalizada a partir de un solo conjunto de reglas existente  
  
1. En el Explorador de soluciones, haga clic en el proyecto y, a continuación, seleccione **propiedades**.  
  
2. En el **propiedades** , haga clic **análisis de código**.  
  
3. En el **Pravidel** lista desplegable, realice una de las siguientes acciones:  
  
   - Seleccione el conjunto de reglas que desee personalizar.  
  
     \- o -  
  
   - Seleccione  **\<Examinar... >** especificar una regla existente conjunto que no está en la lista.  
  
4. Haga clic en **abierto** para mostrar las reglas en el editor de conjunto de reglas.  
  
#### <a name="to-create-a-custom-rule-set-from-multiple-existing-rule-sets"></a>Para crear un conjunto de reglas personalizado a partir de varios conjuntos de reglas existentes  
  
1. En el Explorador de soluciones, haga clic en el proyecto y, a continuación, seleccione **propiedades**.  
  
2. En el **propiedades** , haga clic **análisis de código**.  
  
3. Seleccione  **\<elegir varios conjuntos de reglas... >** desde **ejecutar este conjunto de reglas**.  
  
4. En el **agregar o quitar conjuntos de reglas** cuadro de diálogo, seleccione la regla se establece en que desea basar el nuevo conjunto de reglas y, a continuación, haga clic en **Aceptar**.  
  
5. Guarde el nuevo conjunto de reglas.  
  
     El nombre del nuevo conjunto de reglas está seleccionado en el **ejecutar este conjunto de reglas** lista. Puede cambiar el nombre para mostrar del conjunto de reglas en el paso siguiente.  
  
6. (Opcional) Para cambiar el nombre para mostrar del conjunto de reglas, en el **vista** menú, haga clic en **ventana propiedades**. Escriba el nombre para mostrar en el **nombre** cuadro.  
  
7. Para agregar, quitar, o modificar reglas de análisis de código específico en el nuevo conjunto de reglas, haga clic en **abierto**.  
  
## <a name="modifying-a-rule-set"></a>Modificar un conjunto de reglas  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Para modificar un conjunto de reglas en el editor de conjuntos de reglas  
  
- Para cambiar el nombre para mostrar del conjunto de reglas, en el **vista** menú, haga clic en **ventana propiedades**. Escriba el nombre para mostrar en el **nombre** cuadro. Observe que el nombre para mostrar puede diferir del nombre de archivo.  
  
- Para agregar todas las reglas del grupo a un conjunto de reglas personalizado, active la casilla del grupo. Para quitar todas las reglas del grupo, desactive la casilla.  
  
- Para agregar una regla concreta al conjunto de reglas personalizado, active la casilla de la regla. Para quitar la regla del conjunto de reglas, desactive la casilla.  
  
- Para cambiar la acción realizada cuando se infringe una regla en un análisis de código, haga clic en el **acción** por la regla de campo y, a continuación, seleccione uno de los valores siguientes:  
  
     **Advertir** -genera una advertencia.  
  
     **Error** -genera un error.  
  
     **Ninguno** -deshabilita la regla. Esta acción es igual que quitar la regla del conjunto de reglas.  
  
## <a name="changing-the-rule-set-editor-display"></a>Cambiar la presentación del editor de conjuntos de reglas  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Para agrupar, filtrar o cambiar los campos del editor de conjuntos de reglas mediante la barra de herramientas del editor  
  
- Para expandir las reglas en todos los grupos, haga clic en **Expandir todo**.  
  
- Para contraer las reglas en todos los grupos, haga clic en **Contraer todo**.  
  
- Para cambiar el campo que las reglas se agrupan por, seleccione el campo desde el **Group By** lista. Para mostrar las reglas desagrupadas, seleccione  **\<None >** .  
  
- Para agregar o quitar campos en las columnas de la regla, haga clic en **opciones de columna**.  
  
- Para ocultar reglas que no se aplican a la solución actual, **ocultar reglas que no se aplican a la solución actual**.  
  
- Para alternar entre mostrar y ocultar reglas que tienen asignada la acción de Error, haga clic en **Mostrar reglas que pueden generar errores de análisis de código**.  
  
- Para alternar entre mostrar y ocultar reglas que tienen asignadas la acción advertencia, haga clic en **Mostrar reglas que pueden generar advertencias de análisis de código**.  
  
- Para alternar entre mostrar y ocultar reglas que tienen asignada la **ninguno** acción, haga clic en **Mostrar reglas no habilitadas**.  
  
- Para agregar o quitar conjuntos de reglas predeterminados para el conjunto de reglas actual de Microsoft, haga clic en **agregar o quitar conjuntos de reglas secundarios**.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Configurar análisis de código para un proyecto de código administrado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Referencia del conjunto de reglas Análisis de código](../code-quality/code-analysis-rule-set-reference.md)
