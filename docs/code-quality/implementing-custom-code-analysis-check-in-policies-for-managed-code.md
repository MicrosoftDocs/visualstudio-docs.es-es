---
title: Directivas de protección de análisis de código personalizadas para código administrado
ms.date: 11/04/2016
description: Obtenga información sobre cómo crear una directiva de protección de análisis de código personalizada. Vea cómo asegurarse de que el código administrado de Visual Studio se ajusta a una directiva de proyecto de DevOps de Azure.
ms.custom: SEO-VS-2020
ms.topic: how-to
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 8e682c3d3312be5c4f4639fc2642a398e321fc78
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859884"
---
# <a name="implement-custom-code-analysis-check-in-policies-for-managed-code"></a>Implementar directivas de inserción en el repositorio de análisis de código personalizadas para el código administrado

Una directiva de protección de análisis de código especifica un conjunto de reglas que los miembros de un proyecto de DevOps de Azure deben ejecutarse en el código fuente antes de protegerse en el control de versiones. Microsoft proporciona un conjunto de *conjuntos de reglas* estándar que agrupan las reglas de análisis de código en áreas funcionales. Los *conjuntos de reglas de directivas de inserción en el repositorio personalizadas* especifican un conjunto de reglas de análisis de código que son específicas de un proyecto. Un conjunto de reglas se almacena en un archivo. ruleset.

Las directivas de inserción en el repositorio se establecen en el nivel de proyecto DevOps de Azure y se especifican mediante la ubicación de un archivo. ruleset en el árbol de control de versiones. No hay ninguna restricción en la ubicación de control de versiones del conjunto de reglas personalizadas de directiva de equipo.

El análisis de código se configura para los proyectos de código individuales en la ventana Propiedades de cada proyecto. Un conjunto de reglas personalizado para un proyecto de código se especifica mediante la ubicación física del archivo. ruleset en el equipo local. Cuando se especifica un archivo. ruleset que se encuentra en la misma unidad que el proyecto de código, Visual Studio usa una ruta de acceso relativa al archivo en la configuración del proyecto.

Una práctica recomendada para crear un conjunto de reglas personalizadas del proyecto DevOps de Azure es almacenar el archivo Policy. ruleset de la Directiva de inserción en el repositorio en una carpeta especial que no forma parte de ningún proyecto de código. Si almacena el archivo en una carpeta dedicada, puede aplicar permisos que restrinjan quién puede editar el archivo de reglas, y puede trasladar fácilmente la estructura de directorios que contiene el proyecto a otro directorio o equipo.

## <a name="create-the-project-custom-check-in-rule-set"></a>Crear el conjunto de reglas de protección personalizada del proyecto

Para crear un conjunto de reglas personalizado para un proyecto de DevOps de Azure, primero debe crear una carpeta especial para el conjunto de reglas de la Directiva de protección en **Explorador de control de código fuente**. A continuación, cree el archivo del conjunto de reglas y agréguelo al control de versiones. Por último, especifique el conjunto de reglas como la Directiva de protección del análisis de código para el proyecto.

> [!NOTE]
> Para crear una carpeta en un proyecto de DevOps de Azure, primero debe asignar la raíz del proyecto a una ubicación en el equipo local.

### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Para crear la carpeta de control de versiones para el conjunto de reglas de la Directiva de inserción en el repositorio

1. En Team Explorer, expanda el nodo del proyecto y, a continuación, haga clic en **control de código fuente**.

2. En el panel **carpetas** , haga clic con el botón secundario en el proyecto y, a continuación, haga clic en **nueva carpeta**.

3. En el panel principal de control de código fuente, haga clic con el botón secundario en **nueva carpeta**, haga clic en **cambiar nombre** y escriba un nombre para la carpeta del conjunto de reglas.

### <a name="to-create-the-check-in-policy-rule-set"></a>Para crear el conjunto de reglas de la Directiva de inserción en el repositorio

1. En el menú **Archivo** , elija **Nuevo** y haga clic en **Archivo**.

2. En la lista **categorías** , haga clic en **General**.

3. En la lista **plantillas** , haga doble clic en **conjunto de reglas de análisis de código**.

4. [Especifique las reglas](../code-quality/how-to-create-a-custom-rule-set.md) que se van a incluir en el conjunto de reglas y, a continuación, guarde el archivo del conjunto de reglas en la carpeta del conjunto de reglas que ha creado.

### <a name="to-add-the-rule-set-file-to-version-control"></a>Para agregar el archivo de conjunto de reglas al control de versiones

1. En **Explorador de control de código fuente**, haga clic con el botón secundario en la nueva carpeta y, a continuación, haga clic en **Agregar elementos a la carpeta**.

     Para obtener más información, vea [git y Azure Repos](/azure/devops/repos/git/overview?view=vsts&preserve-view=true).

2. Haga clic en el archivo de conjunto de reglas que creó y, a continuación, haga clic en **Finalizar**.

     El archivo se agrega al control de código fuente y se retira del repositorio.

3. En la ventana detalles de **Explorador de control de código fuente** , haga clic con el botón secundario en el nombre de archivo y, a continuación, haga clic en **proteger los cambios pendientes**.

4. En el cuadro de diálogo de **inserción en el repositorio** , tiene la opción de agregar un comentario y, a continuación, hacer clic en **proteger**.

    > [!NOTE]
    > Si ya ha configurado una directiva de protección de análisis de código para el proyecto de Azure DevOps y ha seleccionado la **opción exigir protección para que solo contenga los archivos que forman parte de la solución actual**, se desencadenará una advertencia de error de directiva. En el cuadro de diálogo error de Directiva, seleccione **invalidar error de directiva y continuar la protección**. Agregue un comentario obligatorio y, a continuación, haga clic en **Aceptar**.

### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Para especificar el archivo de conjunto de reglas como la Directiva de inserción en el repositorio

1. En el menú **equipo** , seleccione **configuración del proyecto** y, a continuación, haga clic en control de **código fuente**.

2. Haga clic en **Directiva de protección** y, a continuación, haga clic en **Agregar**.

3. En la lista **Directiva de protección** , haga doble clic en **análisis de código** y asegúrese de que la casilla **aplicar análisis de código para código administrado** está activada.

4. En la lista **ejecutar este conjunto de reglas** , haga clic en **\<Select Rule Set from Source Control>** .

5. Escriba la ruta de acceso del archivo del conjunto de reglas de la Directiva de protección en el control de versiones.

     La ruta de acceso debe cumplir la siguiente sintaxis:

     **$/** `TeamProjectName` **/** `VersionControlPath`

    > [!NOTE]
    > Puede copiar la ruta de acceso mediante uno de los procedimientos siguientes en **Explorador de control de código fuente**:

    - En el panel **carpetas** , haga clic en la carpeta que contiene el archivo de conjunto de reglas. Copie la ruta de acceso de control de versiones de la carpeta que aparece en el cuadro **origen** y escriba el nombre del archivo de conjunto de reglas manualmente.

    - En la ventana de detalles, haga clic con el botón secundario en el archivo de conjunto de reglas y, a continuación, haga clic en **propiedades**. En la pestaña **General** , copie el valor de **nombre del servidor**.

## <a name="synchronize-code-projects-to-the-check-in-policy-rule-set"></a>Sincronizar proyectos de código con el conjunto de reglas de la Directiva de inserción en el repositorio

Especifique un conjunto de reglas de directiva de protección del proyecto como conjunto de reglas de análisis de código de una configuración de proyecto de código en el cuadro de diálogo Propiedades del proyecto de código. Si el conjunto de reglas se encuentra en la misma unidad que el proyecto de código, se utiliza una ruta de acceso relativa para especificar el conjunto de reglas cuando se selecciona la ruta de acceso en el cuadro de diálogo de archivo. La ruta de acceso relativa permite que las configuraciones de las propiedades del proyecto sean portables a otros equipos que usan estructuras de control de versiones locales similares.

### <a name="to-specify-a-project-rule-set-as-the-rule-set-of-a-code-project"></a>Para especificar un conjunto de reglas de proyecto como conjunto de reglas de un proyecto de código

1. Si es necesario, recupere el archivo y la carpeta del conjunto de reglas de la Directiva de protección del control de versiones.

   Para realizar este paso en **Explorador de control de código fuente** , haga clic con el botón secundario en la carpeta del conjunto de reglas y, a continuación, haga clic en **obtener la última versión**.

2. En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto de código y, a continuación, haga clic en **propiedades**.

3. **Haga clic en análisis de código**.

4. Si es necesario, haga clic en las opciones adecuadas en las listas **configuración** y **plataforma** .

::: moniker range="vs-2017"

5. Para ejecutar el análisis de código cada vez que se compila el proyecto de código con la configuración especificada, seleccione **Habilitar análisis de código al compilar**.

::: moniker-end

::: moniker range=">=vs-2019"

5. Para ejecutar el análisis de código cada vez que se compila el proyecto de código con la configuración especificada, seleccione **ejecutar en la compilación** en la sección **analizadores binarios** .

::: moniker-end

6. En la lista **ejecutar este conjunto de reglas** , haga clic en **\<Browse>** .

8. Seleccione la versión local del archivo del conjunto de reglas de la Directiva de inserción en el repositorio.
