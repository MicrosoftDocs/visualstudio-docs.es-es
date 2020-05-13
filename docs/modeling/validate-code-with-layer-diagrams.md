---
title: Validación código con diagramas de dependencia
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, validating
- validation, dependency diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, dependency diagrams
- MSBuild, validating code
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 975fe8eac5657e245027a4811e50bbc93528cfe5
ms.sourcegitcommit: 273b657e115c1756adb84e0e56b6f2c709bcee76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/07/2020
ms.locfileid: "80759700"
---
# <a name="validate-code-with-dependency-diagrams"></a>Validación código con diagramas de dependencia

## <a name="why-use-dependency-diagrams"></a>¿Por qué usar diagramas de dependencia?

Para asegurarse de que el código no entre en conflicto con su diseño, valide el código con diagramas de dependencia en Visual Studio. Esto puede ser útil para:

- Busque conflictos entre las dependencias del código y las dependencias en el diagrama de dependencias.

- Encontrar dependencias que podrían verse afectadas por los cambios propuestos.

   Por ejemplo, puede editar el diagrama de dependencias para mostrar posibles cambios en la arquitectura y, a continuación, validar el código para ver las dependencias afectadas.

- Refactorizar o migrar el código a un diseño diferente.

   Encontrar código o dependencias que requieran trabajo al cambiar el código a una arquitectura diferente.

**Requisitos**

- Programa para la mejora

  Para crear un diagrama de dependencias para un proyecto de .NET Core, debe tener Visual Studio 2019 versión 16.2 o posterior.

- Una solución que tiene un proyecto de modelado con un diagrama de dependencia. Este diagrama de dependencias debe estar vinculado a artefactos en proyectos de Visual Basic o de C. Consulte [Crear diagramas de dependencia a partir del código.](../modeling/create-layer-diagrams-from-your-code.md)

Para ver qué ediciones de Visual Studio admiten esta característica, vea Compatibilidad con edition para herramientas de [arquitectura y modelado.](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

Puede validar código manualmente desde un diagrama de dependencia abierto en Visual Studio o desde un símbolo del sistema. También puede validar código automáticamente al ejecutar compilaciones locales o compilaciones de Azure Pipelines. Consulte [Canal 9 Vídeo: Diseñar y validar la arquitectura mediante diagramas](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)de dependencia .

> [!IMPORTANT]
> Si desea ejecutar la validación de capas mediante Team Foundation Server (TFS), también debe instalar la misma versión de Visual Studio en el servidor de compilación.

## <a name="live-dependency-validation"></a>Validación de dependencias en vivo

La validación de dependencias se produce en tiempo real y los errores se muestran inmediatamente en la lista de **errores**.

* La validación en vivo es compatible con C. y Visual Basic.

* Para habilitar el análisis completo de la solución al utilizar la validación de dependencias en vivo, abra la configuración de opciones de la barra de oro que aparece en la **lista**de errores .

  - Puede descartar permanentemente la barra de oro si no está interesado en ver todos los problemas arquitectónicos en su solución.
  - Si no habilita el análisis completo de la solución, el análisis se realiza solo para los archivos que se están editando.

* Al actualizar proyectos para habilitar la validación en vivo, un cuadro de diálogo muestra el progreso de la conversión.

* Al actualizar un proyecto para la validación de dependencias en vivo, la versión del paquete NuGet se actualiza para que sea la misma para todos los proyectos y es la versión más alta en uso.

* Agregar un nuevo proyecto de validación de dependencia desencadena una actualización del proyecto.

## <a name="see-if-an-item-supports-validation"></a>Ver si un elemento admite validación

Puede vincular capas a sitios web, documentos de Office, archivos de texto sin formato y archivos en proyectos que se comparten entre varias aplicaciones, pero el proceso de validación no las incluirá. Los errores de validación no aparecerán para las referencias a proyectos o ensamblados que están vinculados a capas independientes cuando no aparece ninguna dependencia entre esas capas. Tales referencias no se consideran dependencias a menos que el código utilice esas referencias.

1. En el diagrama de dependencias, seleccione una o varias capas, haga clic con el botón derecho en la selección y, a continuación, haga clic en **Ver vínculos**.

2. En el Explorador de **capas**, mire la columna Validación de **soportes.** Si el valor es false, el elemento no admite la validación.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Incluir otros ensamblados y proyectos de .NET para su validación

Al arrastrar elementos al diagrama de dependencias, las referencias a los ensamblados o proyectos de .NET correspondientes se agregan automáticamente a la carpeta **Referencias** de capa del proyecto de modelado. Esta carpeta contiene referencias a los ensamblados y proyectos que se analizan durante la validación. Puede incluir otros ensamblados y proyectos de .NET para su validación sin arrastrarlos manualmente al diagrama de dependencias.

1. En el **Explorador**de soluciones , haga clic con el botón secundario en el proyecto de modelado o en la carpeta **Referencias** de capa y, a continuación, haga clic en **Agregar referencia**.

2. En el cuadro de diálogo **Agregar referencia,** seleccione los ensamblados o proyectos y, a continuación, haga clic en **Aceptar**.

## <a name="validate-code-manually"></a>Validar código manualmente

Si tiene un diagrama de dependencia abierto que está vinculado a elementos de solución, puede ejecutar el comando **Validar** acceso directo desde el diagrama. También puede utilizar el símbolo del sistema para ejecutar el comando **msbuild** con la propiedad personalizada **/p:ValidateArchitecture** establecida en **True**. Por ejemplo, cuando haga cambios en el código, realice la validación de capas con regularidad para detectar pronto los conflictos de dependencia.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Validar código de un diagrama de dependencia abierto

1. Haga clic con el botón derecho en la superficie del diagrama y, a continuación, haga clic en **Validar arquitectura**.

    > [!NOTE]
    > De forma predeterminada, la propiedad Acción de **compilación** del archivo de diagrama de dependencias (.layerdiagram) se establece en **Validar** para que el diagrama se incluya en el proceso de validación.

     La ventana **Lista** de errores informa de los errores que se producen. Para obtener más información acerca de los errores de validación, consulte Solucionar problemas de [validación](#troubleshoot-layer-validation-issues)de capas .

2. Para ver el origen de cada error, haga doble clic en el error en la ventana Lista de **errores.**

    > [!NOTE]
    > Visual Studio puede mostrar un mapa de código en lugar del origen del error. Esto ocurre cuando el código tiene una dependencia en un ensamblado que no se especifica en el diagrama de dependencias o al código le falta una dependencia especificada por el diagrama de dependencias. Revise el mapa de código o el código para determinar si debe existir la dependencia. Para obtener más información acerca de los mapas de código, consulte [Asignar dependencias entre las soluciones.](../modeling/map-dependencies-across-your-solutions.md)

3. Para administrar errores, consulte Resolver errores de [validación](#resolve-layer-validation-errors)de capas .

### <a name="validate-code-at-the-command-prompt"></a>Validar código en el símbolo del sistema

1. Abra el símbolo del sistema de Visual Studio.

2. Elija una de las siguientes opciones:

   - Para validar código en un proyecto de modelado específico de la solución, ejecute MSBuild con la siguiente propiedad personalizada.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - O bien

       Vaya a la carpeta que contiene el archivo de proyecto de modelado (.modelproj) y el diagrama de dependencias y, a continuación, ejecute MSBuild con la siguiente propiedad personalizada:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Para validar código en todos los proyectos de modelado de la solución, ejecute MSBuild con la siguiente propiedad personalizada:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - O bien

       Vaya a la carpeta de la solución, que debe contener un proyecto de modelado que contenga un diagrama de dependenciay, a continuación, ejecute MSBuild con la siguiente propiedad personalizada:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Se mostrará cualquier error que se produzca. Para obtener más información acerca de MSBuild, vea [MSBuild](../msbuild/msbuild.md) y [MSBuild Task](../msbuild/msbuild-task.md).

   Para obtener más información acerca de los errores de validación, consulte Solucionar problemas de [validación](#troubleshoot-layer-validation-issues)de capas .

### <a name="manage-validation-errors"></a>Administrar errores de validación

Durante el proceso de desarrollo, puede que desee suprimir algunos de los conflictos notificados durante la validación. Por ejemplo, es posible que desee suprimir errores de los que ya se ha ocupado o que no son pertinentes para su escenario concreto. Cuando se suprime un error, se recomienda registrar un elemento de trabajo en Team Foundation.

> [!WARNING]
> Ya debe estar conectado al control de código fuente TFS (SCC) para crear o vincular a un elemento de trabajo. Si intenta abrir una conexión a un SCC TFS diferente, Visual Studio cierra automáticamente la solución actual. Asegúrese de que ya está conectado al SCC apropiado antes de intentar crear o vincular a un elemento de trabajo. En las versiones posteriores de Visual Studio, los comandos de menú no están disponibles si no está conectado a un SCC.

#### <a name="create-a-work-item-for-a-validation-error"></a>Crear un elemento de trabajo para un error de validación

- En la ventana **Lista** de errores, haga clic con el botón derecho en el error, seleccione **Crear elemento de trabajo**y, a continuación, haga clic en el tipo de elemento de trabajo que desea crear.

Utilice estas tareas para administrar los errores de validación en la ventana Lista de **errores:**

|**To**|**Siga estos pasos**|
|-|-|
|Suprimir los errores seleccionados durante la validación|Haga clic con el botón derecho en uno o varios errores seleccionados, seleccione Administrar errores de **validación**y, a continuación, haga clic en **Suprimir errores**.<br /><br /> Los errores suprimidos aparecen tachados. La próxima vez que ejecute la validación, estos errores no aparecerán.<br /><br /> Se realiza un seguimiento de los errores suprimidos en un archivo .suppressions para el archivo de diagrama de dependencia correspondiente.|
|Detener la supresión de los errores seleccionados|Haga clic con el botón derecho en el error o errores suprimidos seleccionados, seleccione Administrar errores de **validación**y, a continuación, haga clic en **Detener supresión de errores**.<br /><br /> La próxima vez que ejecute la validación, los errores suprimidos aparecerán.|
|Restaurar todos los errores suprimidos en la ventana Lista de **errores**|Haga clic con el botón derecho en cualquier lugar de la ventana **Lista** de errores, seleccione Administrar errores de **validación**y, a continuación, haga clic en **Mostrar todos los errores suprimidos**.|
|Ocultar todos los errores suprimidos de la ventana Lista de **errores**|Haga clic con el botón derecho en cualquier lugar de la ventana **Lista** de errores, seleccione Administrar errores de **validación**y, a continuación, haga clic en **Ocultar todos los errores suprimidos**.|

## <a name="validate-code-automatically"></a>Validar código automáticamente

Puede realizar la validación de capas cada vez que ejecute una compilación local. Si su equipo usa VSTS, puede realizar la validación de capas con registros bloqueados, que puede especificar mediante la creación de una tarea de MSBuild personalizada y usar informes de compilación para recopilar errores de validación. Para crear compilaciones de protección privada, consulte [Protección de registro sin TFVC](/azure/devops/pipelines/build/triggers).

### <a name="to-validate-code-automatically-during-a-local-build"></a>Para validar código automáticamente durante una compilación local

Use un editor de texto para abrir el archivo del proyecto de modelado (.modelproj) y, a continuación, incluya la siguiente propiedad:

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- o -

1. En el **Explorador**de soluciones , haga clic con el botón secundario en el proyecto de modelado que contiene el diagrama o diagramas de dependencia y, a continuación, haga clic en **Propiedades**.

2. En la ventana **Propiedades,** establezca la propiedad **Validar arquitectura** del proyecto de modelado en **True**.

    Esto incluye el proyecto de modelado en el proceso de validación.

3. En el Explorador de **soluciones**, haga clic en el archivo de diagrama de dependencias (.layerdiagram) que desea usar para la validación.

4. En la ventana **Propiedades,** asegúrese de que la propiedad Acción de **compilación** del diagrama está establecida en **Validar**.

    Esto incluye el diagrama de dependencias en el proceso de validación.

Para administrar errores en la ventana Lista de errores, consulte Resolver errores de [validación](#resolve-layer-validation-errors)de capas .

## <a name="troubleshoot-layer-validation-issues"></a>Solucionar problemas de validación de capas

En la siguiente tabla se describen problemas de validación de capas y su resolución. Estos problemas difieren de los errores que son resultado de conflictos entre el código y el diseño. Para obtener más información acerca de estos errores, consulte Solucionar problemas de [validación](#troubleshoot-layer-validation-issues)de capas .

|**Problema**|**Posible causa**|**Resolución**|
|-|-|-|
|Los errores de validación no se producen como se espera.|La validación no funciona en diagramas de dependencia que se copian de otros diagramas de dependencia en el Explorador de soluciones y que se encuentran en el mismo proyecto de modelado. los diagramas de dependencia que se copian de esta manera contienen las mismas referencias que el diagrama de dependencia original.|Agregue un nuevo diagrama de dependencias al proyecto de modelado.<br /><br /> Copie los elementos del diagrama de dependencia de origen en el nuevo diagrama.|

## <a name="resolve-layer-validation-errors"></a>Resolver errores de validación de capas

Al validar código con un diagrama de dependencias, se producen errores de validación cuando el código entra en conflicto con el diseño. Por ejemplo, las siguientes condiciones podrían producir errores de validación:

- Un artefacto se ha asignado a la capa equivocada. En este caso, mueva el artefacto.

- Un artefacto, como por ejemplo una clase, usa otra clase de forma que hay conflictos con su arquitectura. En este caso, tiene que refactorizar el código para quitar la dependencia.

Para resolver estos errores, actualice el código hasta no aparezcan más errores durante la validación. Puede realizar esta tarea repetitivamente.

En la sección siguiente se describe la sintaxis que se usa en estos errores, se explica el significado de los mismos y se sugiere qué se puede hacer para resolverlos o administrarlos.

|**Sintaxis**|**Descripción**|
|-|-|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* es un artefacto que está asociado a una capa en el diagrama de dependencias.<br /><br /> *ArtifactTypeN* es el tipo de *ArtifactN*, como una **clase** o **un método**, por ejemplo:<br /><br /> MiSolución.MiProyecto.MiClase.MiMétodo(Método)|
|*NamespaceNameN*|Nombre de un espacio de nombres.|
|*LayerNameN*|El nombre de una capa en el diagrama de dependencias.|
|*DependencyType*|El tipo de relación de dependencia entre *Artifact1* y *Artifact2*. Por ejemplo, *Artifact1* tiene una relación **Calls** con *Artifact2*.|

| **Sintaxis del error** | **Descripción del error** |
|-|-|
| DV0001: **Dependencia no válida** | Este problema se notifica cuando un elemento de código (espacio de nombres, tipo, miembro) asignado a una capa hace referencia a un elemento de código asignado a otra capa, pero no hay ninguna flecha de dependencia entre estas capas en el diagrama de validación de dependencias que contiene estas capas. Se trata de una infracción de restricción de dependencia. |
| DV1001: Nombre de espacio de **nombres no válido** | Este problema se notifica en un elemento de código asociado a una capa que la propiedad "Nombres de espacio de nombres permitidos" no contiene el espacio de nombres en el que se define este elemento de código. Se trata de una infracción de restricción de nomenclatura. Tenga en cuenta que la sintaxis de "Nombres de espacio de nombres permitidos" debe ser una lista de punto y coma de espacios de nombres en los que se permite definir los elementos de código asociados a la capa. |
| DV1002: Dependencia del espacio de **nombres que no se puede hacer referencia** | Este problema se notifica en un elemento de código asociado a una capa y hace referencia a otro elemento de código definido en un espacio de nombres que se define en la propiedad "Espacio de nombres no referenciable" de la capa. Se trata de una infracción de restricción de nomenclatura. Tenga en cuenta que la propiedad "Espacios de nombres no referenciables" se define como una lista separada por punto y coma de espacios de nombres a los que no se debe hacer referencia en los elementos de código asociados a esta capa. |
| DV1003: Nombre de espacio de **nombres no permitido** | Este problema se notifica en un elemento de código asociado a una capa que la propiedad "Nombres de espacio de nombres no permitidos" contiene el espacio de nombres en el que se define este elemento de código. Se trata de una infracción de restricción de nomenclatura. Tenga en cuenta que la propiedad "Nombre de espacio de nombres no permitido" se define como una lista separada por punto y coma de espacios de nombres en los que no se deben definir los elementos de código asociados a esta capa. |
| DV2001: Presencia de diagrama de **capas** | Este problema se notifica en un proyecto que no incluye un archivo de diagrama de dependencia, pero hace referencia a los analizadores de validación de dependencias. Si no se ha utilizado la validación de dependencias, puede quitar "Microsoft.DependencyValidation.Analyzers" directamente del Explorador de soluciones o suprimir esta advertencia. Para agregar un diagrama de dependencias, consulte [Crear diagramas de dependencia a partir del código.](../modeling/create-layer-diagrams-from-your-code.md) |
| DV2002: Base de **tipos sin asignar** | Este problema se notifica cuando un elemento de código no se asigna a ninguna capa. |
| DV3001: **Falta enlace** | Capa '*LayerName*' enlaces a '*Artifact*' que no se puede encontrar. ¿Falta una referencia de ensamblado? |
| DV9001: **El análisis arquitectónico encontró errores internos** | Puede que los resultados no estén completos. Vea el registro detallado de eventos de compilación o la ventana de salida para obtener más información. |

## <a name="see-also"></a>Consulte también

- [Validación de dependencias en vivo en Visual Studio](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [Validar el sistema durante el desarrollo](../modeling/validate-your-system-during-development.md)
- [Vídeo: Valide sus dependencias de arquitectura en tiempo real](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
