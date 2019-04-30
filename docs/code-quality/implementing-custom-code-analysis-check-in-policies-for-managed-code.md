---
title: Implementar directivas de protección de análisis de código personalizadas para el código administrado
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c32164ef319199171b75379823dc021cfd886d74
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62815795"
---
# <a name="implement-custom-code-analysis-check-in-policies-for-managed-code"></a>Implementar directivas de inserción en el repositorio de análisis de código personalizadas para el código administrado

Una directiva de protección de análisis de código especifica un conjunto de reglas que se deben ejecutar los miembros de un proyecto de DevOps de Azure en el código fuente antes de protegerlo en el control de versiones. Microsoft proporciona un conjunto de estándar *conjuntos de reglas* ese análisis de código de grupo de reglas en las áreas funcionales. *Conjuntos de reglas de directiva de protección personalizadas* especificar un conjunto de reglas de análisis de código que son específicos de un proyecto. Un conjunto de reglas se almacena en un archivo .ruleset.

Las directivas de protección se establece en el nivel de proyecto de DevOps de Azure y especificadas por la ubicación del archivo .ruleset en el árbol de control de versiones. No hay ninguna restricción en la ubicación del control de versión del conjunto de reglas personalizado de la directiva de equipo.

Análisis de código está configurado para los proyectos de código individuales en la ventana Propiedades para cada proyecto. Una regla personalizada establecido para un proyecto de código especificada por la ubicación física del archivo .ruleset en el equipo local. Cuando se especifica un archivo .ruleset que se encuentra en la misma unidad que el proyecto de código, Visual Studio usa una ruta de acceso relativa al archivo en la configuración del proyecto.

Una práctica sugerida para la creación de un conjunto de reglas personalizadas de proyecto consiste en almacenar el archivo .ruleset de directiva de protección en una carpeta especial que no forma parte de cualquier proyecto de código de Azure DevOps. Si almacena el archivo en una carpeta dedicada, puede aplicar permisos restringirán quién pueden editar el archivo de reglas y se puede mover fácilmente la estructura de directorios contiene el proyecto a otro directorio o equipo.

## <a name="create-the-project-custom-check-in-rule-set"></a>Crear el conjunto de reglas personalizado en el repositorio del proyecto

Para crear una regla personalizada establecido para un proyecto de DevOps de Azure, primero se crea una carpeta especial para la regla de directiva de protección se establece **Explorador de Control de código fuente**. A continuación, cree el archivo de conjunto de reglas y agregue el archivo al control de versiones. Por último, especifique el conjunto de reglas como la directiva de comprobación del análisis de código para el proyecto.

> [!NOTE]
> Para crear una carpeta en un proyecto de DevOps de Azure, primero debe asignar la raíz del proyecto a una ubicación en el equipo local.

### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Para crear la carpeta de control de versiones para el conjunto de reglas de directiva de protección

1. En Team Explorer, expanda el nodo del proyecto y, a continuación, haga clic en **Control de código fuente**.

2. En el **carpetas** panel, haga clic en el proyecto y, a continuación, haga clic en **nueva carpeta**.

3. En el panel de Control de código fuente principal, haga clic en **nueva carpeta**, haga clic en **cambiar el nombre**y escriba un nombre para la regla del conjunto de carpetas.

### <a name="to-create-the-check-in-policy-rule-set"></a>Para crear el conjunto de reglas de directiva de protección

1. En el **archivo** menú, elija **New**y, a continuación, haga clic en **archivo**.

2. En el **categorías** lista, haga clic en **General**.

3. En el **plantillas** lista, haga doble clic en **conjunto de reglas de análisis de código**.

4. [Especificar las reglas](../code-quality/how-to-create-a-custom-rule-set.md) incluir en el conjunto de reglas y, a continuación, guardar la regla establece el archivo en la carpeta de conjunto de reglas que ha creado.

### <a name="to-add-the-rule-set-file-to-version-control"></a>Para agregar la regla de conjunto de archivos al control de versiones

1. En **Explorador de Control de código fuente**, haga clic en la nueva carpeta y, a continuación, haga clic en **agregar elementos a la carpeta**.

     Para obtener más información, consulte [Git y repositorios de Azure](/azure/devops/repos/git/overview?view=vsts).

2. Haga clic en la regla establece el archivo que ha creado y, a continuación, haga clic en **finalizar**.

     El archivo se agrega al control de código fuente y desprotegido.

3. En el **Explorador de Control de código fuente** ventana de detalles, haga clic en el nombre de archivo y, a continuación, haga clic en **proteger cambios pendientes**.

4. En el **en el repositorio** cuadro de diálogo, tiene la opción para agregar un comentario y, a continuación, haga clic en **proteger**.

    > [!NOTE]
    > Si ya ha configurado una directiva de protección de análisis de código para un proyecto de DevOps de Azure y ha seleccionado la **exigir la protección para que solo contenga los archivos que forman parte de la solución actual**, se desencadenará una advertencia de error de directiva. En el cuadro de diálogo de error de la directiva, seleccione **invalidar el error de directiva y continuar la protección**. Agregue un comentario necesario y, a continuación, haga clic en **Aceptar**.

### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Para especificar la regla de conjunto de archivos como la directiva de protección

1. En el **equipo** menú, elija **configuración del proyecto**y, a continuación, haga clic en **Control de código fuente**.

2. Haga clic en **directiva de protección**y, a continuación, haga clic en **agregar**.

3. En el **directiva de protección** lista, haga doble clic en **análisis de código**y asegúrese de que el **aplicar análisis de código para código administrado** casilla está activada.

4. En el **ejecutar este conjunto de reglas** lista, haga clic en  **\<Seleccionar conjunto de reglas de Control de código fuente >**.

5. Escriba la ruta de acceso del archivo de conjunto de regla de directiva de protección en el control de versiones.

     La ruta de acceso debe ajustarse a la sintaxis siguiente:

     **$/** `TeamProjectName` **/** `VersionControlPath`

    > [!NOTE]
    > Puede copiar la ruta de acceso mediante uno de los siguientes procedimientos en **Explorador de Control de código fuente**:

    - En el **carpetas** panel, haga clic en la carpeta que contiene el archivo de conjunto de reglas. Copie la ruta de acceso de control de versiones de la carpeta que aparece en el **origen** cuadro y escriba el nombre del archivo de conjunto de reglas manualmente.

    - En la ventana de detalles, haga clic en el archivo de conjunto de reglas y, a continuación, haga clic en **propiedades**. En el **General** pestaña, copie el valor en **nombre del servidor**.

## <a name="synchronize-code-projects-to-the-check-in-policy-rule-set"></a>Sincronizar los proyectos de código con el conjunto de reglas de directiva de protección

Especifique una regla de directiva de protección del proyecto se establece como el conjunto de reglas de análisis de código de una configuración de proyecto de código en el cuadro de diálogo Propiedades del proyecto de código. Si el conjunto de reglas se encuentra en la misma unidad que el proyecto de código, una ruta de acceso relativa se utiliza para especificar el conjunto de reglas cuando se selecciona la ruta de acceso desde el cuadro de diálogo de archivo. Estructuras de control de la ruta de acceso relativa permite que la configuración de propiedades del proyecto que sean portables a otros equipos que usan la versión local similar.

### <a name="to-specify-a-project-rule-set-as-the-rule-set-of-a-code-project"></a>Para especificar una regla de proyecto establece como el conjunto de reglas de un proyecto de código

1. Si es necesario, recuperar la carpeta de conjunto de reglas de directiva de protección y el archivo de control de versiones.

   Puede realizar este paso en **Explorador de Control de código fuente** haciendo la regla establece carpeta y, a continuación, haga clic en **obtener última versión**.

2. En **el Explorador de soluciones**, haga clic en el proyecto de código y, a continuación, haga clic en **propiedades**.

3. **Haga clic en el análisis de código**.

4. Si es necesario, haga clic en las opciones adecuadas en el **configuración** y **plataforma** enumera.

5. Para ejecutar análisis de código cada vez que se compila el proyecto de código con la configuración especificada, seleccione el **Habilitar análisis de código al compilar (define la constante CODE_ANALYSIS)** casilla de verificación.

6. Para omitir el código en componentes de otras empresas, seleccione el **Suprimir resultados del código generado** casilla de verificación.

7. En el **ejecutar este conjunto de reglas** lista, haga clic en  **\<Examinar... >**.

8. Especifique la versión local del archivo de conjunto de regla de directiva de protección.