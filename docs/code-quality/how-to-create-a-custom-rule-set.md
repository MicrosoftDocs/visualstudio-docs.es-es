---
title: Crear un conjunto de reglas de análisis de código personalizado
ms.date: 11/02/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- rule sets
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2f642ea8e41e4a9ccf2b35f432df528fc5e81d0
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65676557"
---
# <a name="customize-a-rule-set"></a>Personalizar un conjunto de reglas

Puede crear una regla personalizada establecida para satisfacer las necesidades concretas del proyecto para el análisis de código.

## <a name="create-a-custom-rule-set-from-an-existing-rule-set"></a>Crear una regla personalizada que se establece desde un conjunto de reglas existente

Para crear una regla personalizada conjunto, puede abrir una regla integrada establecida en el **editor de conjunto de reglas**. Desde allí, puede agregar o quitar reglas concretas, y puede cambiar la acción que se produce cuando se infringe una regla&mdash;por ejemplo, mostrar una advertencia o un error.

1. En **el Explorador de soluciones**, haga clic en el proyecto y, a continuación, seleccione **propiedades**.

2. En el **propiedades** páginas, seleccionadas el **análisis de código** ficha.

3. En el **ejecutar este conjunto de reglas** lista desplegable, realice una de las siguientes acciones:

   - Seleccione el conjunto de reglas que desee personalizar.

     \- o -

   - Seleccione  **\<Examinar... >** especificar una regla existente conjunto que no está en la lista.

4. Seleccione **abierto** para mostrar las reglas en el editor de conjunto de reglas.

> [!NOTE]
> Si tiene un proyecto .NET Core o .NET Standard, el proceso es un poco diferente porque no hay ningún **análisis de código** ficha de propiedades. Siga los pasos para [copiar una regla predefinida establecido en el proyecto y establézcalo como el conjunto de reglas activo](analyzer-rule-sets.md). Después de haber copiado a través de un conjunto de reglas, puede [editar en el editor de conjunto de reglas de Visual Studio](working-in-the-code-analysis-rule-set-editor.md) , ábralo desde **el Explorador de soluciones**.

## <a name="create-a-new-rule-set"></a>Crear un nuevo conjunto de reglas

Puede crear un nuevo archivo de conjunto de reglas desde el **nuevo archivo** cuadro de diálogo:

1. Seleccione **archivo** > **New** > **archivo**, o bien presione **Ctrl**+**N**.

2. En el **nuevo archivo** cuadro de diálogo, seleccione el **General** categoría de la izquierda y, a continuación, seleccione **conjunto de reglas de análisis de código**.

3. Seleccione **abierto**.

   El nuevo *.ruleset* archivo se abre en el editor de conjunto de reglas.

## <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>Crear un conjunto de varios conjuntos de reglas de reglas personalizadas

> [!NOTE]
> El procedimiento siguiente no es aplicable a proyectos de .NET Core, que no tienen un **análisis de código** ficha de propiedades.

1. En **el Explorador de soluciones**, haga clic en el proyecto y, a continuación, seleccione **propiedades**.

2. En el **propiedades** páginas, seleccionadas el **análisis de código** ficha.

3. Seleccione  **\<elegir varios conjuntos de reglas... >** desde **ejecutar este conjunto de reglas**.

4. En el **agregar o quitar conjuntos de reglas** cuadro de diálogo, seleccione los conjuntos de reglas desea incluir en el nuevo conjunto de reglas.

   ![Agregar o quitar el cuadro de diálogo de conjuntos de reglas](media/add-remove-rule-sets.png)

5. Seleccione **Guardar como**, escriba un nombre para el *.ruleset* de archivo y, a continuación, seleccione **guardar**.

   El nuevo conjunto de reglas está seleccionado en el **ejecutar este conjunto de reglas** lista.

6. Seleccione **abrir** para abrir la nueva regla se establece en el editor de conjunto de reglas.

## <a name="rule-precedence"></a>Prioridad de la regla

- Si la misma regla está activa de dos o más veces en un conjunto de reglas con diferentes niveles de gravedad, el compilador genera un error. Por ejemplo:

   ```xml
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" />
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

- Si la misma regla está activa de dos o más veces en un conjunto de reglas con el *mismo* gravedad, es posible que vea la advertencia siguiente en el **lista de errores**:

   **CA0063: No se pudo cargar el archivo de conjunto de reglas '\[su] .ruleset ' o uno de sus reglas dependientes conjunto de archivos. El archivo no se ajusta al esquema del conjunto de reglas.**

- Si el conjunto de reglas incluye un conjunto mediante el uso de reglas secundarios una **Include** etiqueta y los conjuntos de reglas secundarios y primarios tanto la lista de la misma regla pero con diferentes niveles de gravedad, a continuación, la gravedad en el conjunto de reglas primario tiene prioridad. Por ejemplo:

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

Para cambiar el nombre para mostrar de un conjunto de reglas que está abierto en el editor, abra el **propiedades** ventana seleccionando **vista** > **ventana propiedades** en la barra de menús. Escriba el nombre para mostrar en el **nombre** cuadro. También puede escribir una descripción para el conjunto de reglas.

## <a name="next-steps"></a>Pasos siguientes

Ahora que ha configurado una regla, el paso siguiente es personalizar las reglas agregando o quitando reglas o modificando la gravedad de las infracciones de reglas.

> [!div class="nextstepaction"]
> [Modificar las reglas en el editor de conjunto de reglas](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>Vea también

- [Cómo: Configurar análisis de código para un proyecto de código administrado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [Referencia del conjunto de reglas Análisis de código](../code-quality/rule-set-reference.md)