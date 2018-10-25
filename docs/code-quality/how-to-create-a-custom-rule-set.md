---
title: Crear una regla de análisis de código personalizado en Visual Studio
ms.date: 04/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dce43c02f4976b51bab61a48f615fb0307102fc7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884191"
---
# <a name="customize-a-rule-set"></a>Personalizar un conjunto de reglas

Puede crear una regla personalizada establecida para satisfacer las necesidades concretas del proyecto para el análisis de código.

## <a name="create-a-custom-rule-set"></a>Creación de un conjunto de reglas personalizadas

Para crear una regla personalizada conjunto, puede abrir una regla integrada establecida en el **editor de conjunto de reglas**. Desde allí, puede agregar o quitar reglas concretas, y puede cambiar la acción que se produce cuando se infringe una regla&mdash;por ejemplo, mostrar una advertencia o un error.

1. En **el Explorador de soluciones**, haga clic en el proyecto y, a continuación, seleccione **propiedades**.

2. En el **propiedades** páginas, seleccionadas el **análisis de código** ficha.

3. En el **ejecutar este conjunto de reglas** lista desplegable, realice una de las siguientes acciones:

   - Seleccione el conjunto de reglas que desee personalizar.

     \- o -

   - Seleccione  **\<Examinar... >** especificar una regla existente conjunto que no está en la lista.

4. Seleccione **abierto** para mostrar las reglas en el editor de conjunto de reglas.

También puede crear un nuevo archivo de conjunto de reglas desde el **nuevo archivo** cuadro de diálogo:

1. Seleccione **archivo** > **New** > **archivo**, o bien presione **Ctrl**+**N**.

2. En el **nuevo archivo** cuadro de diálogo, seleccione el **General** categoría de la izquierda y, a continuación, seleccione **conjunto de reglas de análisis de código**.

3. Seleccione **abierto**.

   El nuevo *.ruleset* archivo se abre en el editor de conjunto de reglas.

### <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>Crear un conjunto de varios conjuntos de reglas de reglas personalizadas

1. En el Explorador de soluciones, haga clic en el proyecto y, a continuación, seleccione **propiedades**.

2. En el **propiedades** páginas, seleccionadas el **análisis de código** ficha.

3. Seleccione  **\<elegir varios conjuntos de reglas... >** desde **ejecutar este conjunto de reglas**.

4. En el **agregar o quitar conjuntos de reglas** cuadro de diálogo, seleccione los conjuntos de reglas desea incluir en el nuevo conjunto de reglas.

   ![Agregar o quitar el cuadro de diálogo de conjuntos de reglas](media/add-remove-rule-sets.png)

5. Seleccione **Guardar como**, escriba un nombre para el *.ruleset* de archivo y, a continuación, seleccione **guardar**.

   El nuevo conjunto de reglas está seleccionado en el **ejecutar este conjunto de reglas** lista.

6. Seleccione **abrir** para abrir la nueva regla se establece en el editor de conjunto de reglas.

## <a name="name-and-description"></a>Nombre y descripción

Para cambiar el nombre para mostrar de un conjunto de reglas que está abierto en el editor, abra el **propiedades** ventana seleccionando **vista** > **ventana propiedades** en la barra de menús. Escriba el nombre para mostrar en el **nombre** cuadro. También puede escribir una descripción para el conjunto de reglas.

## <a name="next-steps"></a>Pasos siguientes

Ahora que ha configurado una regla, el paso siguiente es personalizar las reglas agregando o quitando reglas o modificar la gravedad de las infracciones de reglas.

> [!div class="nextstepaction"]
> [Modificar las reglas en el editor de conjunto de reglas](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>Vea también

- [Cómo: Configurar el análisis de código para un proyecto de código administrado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [Referencia del conjunto de reglas Análisis de código](../code-quality/rule-set-reference.md)