---
title: Implementar directivas de protección de análisis de código personalizado para el código administrado en Visual Studio
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c50daf82a5dc5774cae75ecab54f1455c1a1c251
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="implement-custom-code-analysis-check-in-policies-for-managed-code"></a>Implementar directivas de protección de análisis de código personalizado para el código administrado

Un directiva de protección especifica un conjunto de reglas que los miembros de un proyecto de equipo deben ejecutar en el código fuente antes de que el análisis de código se comprueba en el control de versiones. Microsoft proporciona un conjunto de standard *conjuntos de reglas* el análisis de código de ese grupo de reglas en áreas funcionales. *Conjuntos de reglas de directiva de protección personalizadas* especificar un conjunto de reglas de análisis de código que son específicos de un proyecto de equipo. Un conjunto de reglas se almacena en un archivo .ruleset.

Directivas de protección se establecen en el nivel de proyecto de equipo y especifica la ubicación de un archivo .ruleset en el árbol de control de versiones. No hay ninguna restricción en la ubicación del control de versión del conjunto de reglas personalizado de la directiva de equipo.

Análisis de código está configurado para los proyectos de código individuales en la ventana Propiedades para cada proyecto. Una regla personalizada establecido para un proyecto de código se especifica mediante la ubicación física del archivo .ruleset en el equipo local. Cuando se especifica un archivo .ruleset que se encuentra en la misma unidad que el proyecto de código, Visual Studio utiliza una ruta de acceso relativa al archivo en la configuración del proyecto.

Es un ejercicio sugerido para crear un conjunto de reglas personalizadas de proyecto de equipo almacenar el archivo .ruleset de directiva de protección de una carpeta especial que no forma parte de cualquier proyecto de código. Si almacena el archivo en una carpeta dedicada, puede aplicar permisos que restrinjan quién pueden editar el archivo de regla y se puede mover fácilmente la estructura de directorios contiene el proyecto a otro directorio o equipo.

## <a name="create-the-team-project-custom-check-in-rule-set"></a>Crear el conjunto de reglas personalizado en el repositorio del proyecto de equipo

Para crear una regla personalizada establecido para un proyecto de equipo, primero se crea una carpeta especial para la regla de directiva de protección establecida en **Explorador de Control de código fuente**. A continuación, crear el archivo de conjunto de reglas y agregue el archivo al control de versiones. Por último, especifique el conjunto de reglas como la directiva de comprobación del análisis de código del proyecto de equipo.

> [!NOTE]
> Para crear una carpeta en un proyecto de equipo, primero debe asignar la raíz del proyecto de equipo a una ubicación en el equipo local.

### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Para crear la carpeta de control de versiones para el conjunto de reglas de directiva de protección

1. En Team Explorer, expanda el nodo de proyecto de equipo y, a continuación, haga clic en **Control de código fuente**.

2. En el **carpetas** panel, haga clic en el proyecto de equipo y, a continuación, haga clic en **nueva carpeta**.

3. En el panel de Control de código fuente principal, haga clic en **nueva carpeta**, haga clic en **cambiar el nombre de**y escriba un nombre para la regla del conjunto de carpetas.

### <a name="to-create-the-check-in-policy-rule-set"></a>Para crear el conjunto de reglas de directiva de protección

1. En el **archivo** menú, elija **New**y, a continuación, haga clic en **archivo**.

2. En el **categorías** lista, haga clic en **General**.

3. En el **plantillas** lista, haga doble clic en **conjunto de reglas de análisis de código**.

4. [Especifique las reglas](../code-quality/how-to-create-a-custom-rule-set.md) para incluir en el conjunto de reglas y, a continuación, guardar la regla de archivo del conjunto a la carpeta de conjunto de reglas que ha creado.

### <a name="to-add-the-rule-set-file-to-version-control"></a>Para agregar la regla de conjunto de archivos al control de versiones

1. En **Explorador de Control de código fuente**, haga clic en la nueva carpeta y, a continuación, haga clic en **agregar elementos a la carpeta**.

     Para obtener más información, consulte [Git y VSTS](/vsts/git/overview).

2. Haga clic en el conjunto de reglas archivo que creó y, a continuación, haga clic en **finalizar**.

     El archivo se agrega al control de código fuente y se encuentre desprotegido.

3. En el **Explorador de Control de código fuente** ventana de detalles, haga clic en el nombre de archivo y, a continuación, haga clic en **proteger cambios pendientes**.

4. En el **en el repositorio** cuadro de diálogo, tiene la opción para agregar un comentario y, a continuación, haga clic en **proteger**.

    > [!NOTE]
    > Si ya ha configurado una directiva de protección de análisis de código para el proyecto de equipo y ha seleccionado la **aplicar en el repositorio para que sólo contenga los archivos que forman parte de la solución actual**, se desencadenará una advertencia de error de directiva. En el cuadro de diálogo de error de la directiva, seleccione **reemplazar error de directiva y continuar la protección**. Agregue un comentario obligatorio y, a continuación, haga clic en **Aceptar**.

### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Para especificar la regla de conjunto de archivos como la directiva de protección

1. En el **equipo** menú, elija **configuración del proyecto de equipo**y, a continuación, haga clic en **Control de código fuente**.

2. Haga clic en **directiva de protección**y, a continuación, haga clic en **agregar**.

3. En el **directiva de protección** lista, haga doble clic en **análisis de código**y asegúrese de que el **Exigir análisis de código para código administrado** casilla está activada.

4. En el **ejecutar este conjunto de reglas** lista, haga clic en  **\<Seleccionar conjunto de reglas de Control de código fuente >**.

5. Escriba la ruta de acceso del archivo de conjunto de regla de directiva de protección en el control de versiones.

     La ruta de acceso debe seguir la sintaxis siguiente:

     **$/** `TeamProjectName` **/** `VersionControlPath`

    > [!NOTE]
    > Puede copiar la ruta de acceso mediante uno de los siguientes procedimientos en **Explorador de Control de código fuente**:

    - En el **carpetas** panel, haga clic en la carpeta que contiene el archivo de conjunto de reglas. Copie la ruta de acceso de control de versiones de la carpeta que aparece en el **origen** cuadro y escriba el nombre del archivo de conjunto de reglas manualmente.

    - En la ventana de detalles, haga clic en el archivo de conjunto de reglas y, a continuación, haga clic en **propiedades**. En el **General** ficha, copie el valor en **nombre del servidor**.

## <a name="synchronize-code-projects-to-the-check-in-policy-rule-set"></a>Sincronizar proyectos de código con el conjunto de reglas de directiva de protección

Especifique una regla de directiva de protección del proyecto de equipo se establece como el conjunto de reglas de análisis de código de una configuración de proyecto de código en el cuadro de diálogo de propiedades del proyecto de código. Si el conjunto de reglas se encuentra en la misma unidad que el proyecto de código, una ruta de acceso relativa se utiliza para especificar el conjunto de reglas cuando se selecciona la ruta de acceso en el cuadro de diálogo de archivo. Estructuras de control de la ruta de acceso relativa permite la configuración de propiedades del proyecto que sean portables a otros equipos que usan versiones locales similares.

### <a name="to-specify-a-team-project-rule-set-as-the-rule-set-of-a-code-project"></a>Para especificar una regla de proyecto de equipo establecido como el conjunto de reglas de un proyecto de código

1. Si es necesario, recuperar la carpeta del conjunto de reglas de directiva de protección y el archivo de control de versiones.

   Puede realizar este paso en **Explorador de Control de código fuente** haciendo clic en el conjunto de reglas de carpeta y, a continuación, haga clic en **obtener última versión**.

2. En **el Explorador de soluciones**, haga clic en el proyecto de código y, a continuación, haga clic en **propiedades**.

3. **Haga clic en el análisis de código**.

4. Si es necesario, haga clic en las opciones adecuadas en el **configuración** y **plataforma** enumera.

5. Para ejecutar el análisis de código cada vez que se compila el proyecto de código con la configuración especificada, seleccione el **Habilitar análisis de código al compilar (define la constante CODE_ANALYSIS)** casilla de verificación.

6. Para pasar por alto el código en componentes de otras empresas, seleccione la **Suprimir resultados del código generado** casilla de verificación.

7. En el **ejecutar este conjunto de reglas** lista, haga clic en  **\<Examinar... >**.

8. Especifique la versión local del archivo de conjunto de regla de directiva de protección.