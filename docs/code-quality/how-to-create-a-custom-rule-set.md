---
title: Crear un conjunto de reglas de análisis de código personalizado
ms.date: 11/02/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9f23b2badb40effd4222e21ab9e67b2907513c2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587555"
---
# <a name="customize-a-rule-set"></a>Personalización de un conjunto de reglas

Puede crear un conjunto de reglas personalizado para satisfacer las necesidades específicas del proyecto para el análisis de código.

## <a name="create-a-custom-rule-set-from-an-existing-rule-set"></a>Crear un conjunto de reglas personalizado a partir de un conjunto de reglas existente

Para crear un conjunto de reglas personalizado, puede abrir un conjunto de reglas integrado en el **Editor de conjuntos de reglas**. Desde allí, puede Agregar o quitar reglas específicas y puede cambiar la acción que se produce cuando se infringe una regla&mdash;por ejemplo, mostrar una advertencia o un error.

1. En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto y seleccione **propiedades**.

2. En las páginas de **propiedades** , seleccione la pestaña **análisis de código** .

::: moniker range="vs-2017"

3. En la lista desplegable **ejecutar este conjunto de reglas** , realice una de las acciones siguientes:

::: moniker-end

::: moniker range=">=vs-2019"

3. En la lista desplegable **reglas activas** , realice una de las acciones siguientes:

::: moniker-end

   - Seleccione el conjunto de reglas que desee personalizar.

     \- o -

   - Seleccione **\<examinar >** para especificar un conjunto de reglas existente que no esté en la lista.

4. Seleccione **abrir** para mostrar las reglas en el editor de conjuntos de reglas.

> [!NOTE]
> Si tiene un proyecto de .NET Core o .NET Standard, el proceso es un poco diferente porque no hay ninguna pestaña de propiedades de **análisis de código** . Siga los pasos para [copiar un conjunto de reglas predefinido en el proyecto y establézcalo como conjunto de reglas activo](analyzer-rule-sets.md). Después de copiar un conjunto de reglas, puede [editarlo en el editor de conjuntos de reglas de Visual Studio](working-in-the-code-analysis-rule-set-editor.md) abriéndolo desde **Explorador de soluciones**.

## <a name="create-a-new-rule-set"></a>Crear un nuevo conjunto de reglas

Puede crear un nuevo archivo de conjunto de reglas desde el cuadro de diálogo **nuevo archivo** :

1. Seleccione **archivo** > **nuevo** **archivo**de > o presione **Ctrl**+**N**.

2. En el cuadro de diálogo **nuevo archivo** , seleccione la categoría **General** de la izquierda y, a continuación, seleccione **conjunto de reglas de análisis de código**.

3. Seleccione **Abrir**.

   El nuevo archivo *. ruleset* se abre en el editor de conjuntos de reglas.

## <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>Creación de un conjunto de reglas personalizado a partir de varios conjuntos de reglas

> [!NOTE]
> El procedimiento siguiente no se aplica a los proyectos de .NET Core, que no tienen una pestaña de propiedades de **análisis de código** .

1. En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto y seleccione **propiedades**.

2. En las páginas de **propiedades** , seleccione la pestaña **análisis de código** .

::: moniker range="vs-2017"

3. Seleccione **\<elegir varios conjuntos de reglas >** de **ejecutar este conjunto de reglas**.

::: moniker-end

::: moniker range=">=vs-2019"

3. Seleccione **\<elegir varios conjuntos de reglas >** de **reglas activas**.

::: moniker-end

4. En el cuadro de diálogo **Agregar o quitar conjuntos de reglas** , seleccione los conjuntos de reglas que desea incluir en el nuevo conjunto de reglas.

   ![Cuadro de diálogo Agregar o quitar conjuntos de reglas](media/add-remove-rule-sets.png)

5. Seleccione **Guardar como**, escriba un nombre para el archivo *. ruleset* y, a continuación, seleccione **Guardar**.

   El nuevo conjunto de reglas se selecciona en la lista **ejecutar este conjunto de reglas** .

6. Seleccione **abrir** para abrir el conjunto de reglas nuevo en el editor de conjuntos de reglas.

## <a name="rule-precedence"></a>Prioridad de la regla

- Si se muestra la misma regla dos o más veces en un conjunto de reglas con distintos niveles de gravedad, el compilador genera un error. Por ejemplo:

   ```xml
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" />
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

- Si se muestra la misma regla dos o más veces en un conjunto de reglas con la *misma* gravedad, puede ver la siguiente advertencia en el **lista de errores**:

   **CA0063: no se pudo cargar el archivo de conjunto de reglas '\[el]. ruleset ' o uno de sus archivos de conjunto de reglas dependientes. El archivo no se ajusta al esquema del conjunto de reglas.**

- Si el conjunto de reglas incluye un conjunto de reglas secundarias mediante una etiqueta **include** , y la regla secundaria y primaria establece ambas listas en la misma regla pero con diferentes gravedades, la gravedad del conjunto de reglas primario tiene prioridad. Por ejemplo:

   ```xml
   <!-- Parent rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Include Path="classlibrary_child.ruleset" Action="Default" />
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" /> <!-- Overrides CA1021 severity from child rule set -->
     </Rules>
   </RuleSet>

   <!-- Child rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules from child" Description="Code analysis rules from child." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

## <a name="name-and-description"></a>Nombre y descripción

Para cambiar el nombre para mostrar de un conjunto de reglas abierto en el editor, abra la ventana **propiedades** . para ello, seleccione **Ver** > **ventana Propiedades** en la barra de menús. Escriba el nombre para mostrar en el cuadro **nombre** . También puede escribir una descripción para el conjunto de reglas.

## <a name="next-steps"></a>Pasos siguientes

Ahora que tiene un conjunto de reglas, el siguiente paso es personalizar las reglas mediante la adición o eliminación de reglas o la modificación de la gravedad de las infracciones de las reglas.

> [!div class="nextstepaction"]
> [Modificar reglas en el editor de conjuntos de reglas](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>Vea también

- [Cómo: Configurar el análisis de código para un proyecto de código administrado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [Referencia del conjunto de reglas Análisis de código](../code-quality/rule-set-reference.md)
