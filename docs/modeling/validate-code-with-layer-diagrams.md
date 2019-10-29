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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9fc852b4d5003cf809248c72ca3ac42ad3a6bf23
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981131"
---
# <a name="validate-code-with-dependency-diagrams"></a>Validación código con diagramas de dependencia

## <a name="why-use-dependency-diagrams"></a>¿Por qué usar diagramas de dependencia?

Para asegurarse de que el código no entra en conflicto con su diseño, valide el código con diagramas de dependencia en Visual Studio. Esto puede ser útil para:

- Busque conflictos entre las dependencias del código y las dependencias del diagrama de dependencia.

- Encontrar dependencias que podrían verse afectadas por los cambios propuestos.

   Por ejemplo, puede editar el diagrama de dependencia para mostrar los posibles cambios de arquitectura y, a continuación, validar el código para ver las dependencias afectadas.

- Refactorizar o migrar el código a un diseño diferente.

   Encontrar código o dependencias que requieran trabajo al cambiar el código a una arquitectura diferente.

**Requisitos**

- Programa para la mejora

  Para crear un diagrama de dependencia para un proyecto de .NET Core, debe tener Visual Studio 2019 versión 16,2 o posterior.

- Solución que tiene un proyecto de modelado con un diagrama de dependencia. Este diagrama de dependencia debe estar vinculado a artefactos de C# o Visual Basic proyectos que desea validar. Vea [crear diagramas de dependencia desde el código](../modeling/create-layer-diagrams-from-your-code.md).

Para ver qué ediciones de Visual Studio admiten esta característica, vea [compatibilidad de la edición con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Puede validar el código manualmente desde un diagrama de dependencias abierto en Visual Studio o desde el símbolo del sistema. También puede validar el código automáticamente al ejecutar compilaciones locales o compilaciones Azure Pipelines. Consulte [vídeo de Channel 9: diseñar y validar la arquitectura mediante diagramas de dependencia](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture).

> [!IMPORTANT]
> Si desea ejecutar la validación de capas mediante Team Foundation Server (TFS), también debe instalar la misma versión de Visual Studio en el servidor de compilación.

## <a name="live-dependency-validation"></a>Validación de dependencias en vivo

La validación de dependencias se produce en tiempo real y los errores se muestran inmediatamente en el **lista de errores**.

* La validación en C# directo es compatible con y Visual Basic.

* Para habilitar el análisis completo de la solución cuando se usa la validación de dependencias dinámicas, abra la configuración de opciones de la barra dorada que aparece en el **lista de errores**.

  - Puede descartar permanentemente la barra dorada si no está interesado en ver todos los problemas de arquitectura de la solución.
  - Si no habilita el análisis completo de la solución, el análisis se realiza solo para los archivos que se están editando.

* Al actualizar proyectos para habilitar la validación en directo, un cuadro de diálogo muestra el progreso de la conversión.

* Al actualizar un proyecto para la validación de dependencias dinámicas, la versión del paquete NuGet se actualiza para que sea la misma para todos los proyectos y es la versión más alta en uso.

* Al agregar un nuevo proyecto de validación de dependencia, se desencadena una actualización del proyecto.

## <a name="see-if-an-item-supports-validation"></a>Ver si un elemento admite validación

Puede vincular capas a sitios web, documentos de Office, archivos de texto sin formato y archivos de proyectos que se comparten entre varias aplicaciones, pero el proceso de validación no los incluirá. Los errores de validación no aparecerán para las referencias a proyectos o ensamblados que están vinculados a capas independientes cuando no aparece ninguna dependencia entre esas capas. Tales referencias no se consideran dependencias a menos que el código utilice esas referencias.

1. En el diagrama de dependencias, seleccione una o varias capas, haga clic con el botón secundario en la selección y, a continuación, haga clic en **ver vínculos**.

2. En el **Explorador de capas**, examine la columna **admite validación** . Si el valor es false, el elemento no admite la validación.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Incluir otros ensamblados y proyectos de .NET para su validación

Al arrastrar elementos al diagrama de dependencia, las referencias a los ensamblados o proyectos .NET correspondientes se agregan automáticamente a la carpeta **referencias de capa** del proyecto de modelado. Esta carpeta contiene referencias a los ensamblados y proyectos que se analizan durante la validación. Puede incluir otros ensamblados y proyectos de .NET para la validación sin arrastrarlos manualmente al diagrama de dependencia.

1. En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto de modelado o en la carpeta **referencias de capa** y, a continuación, haga clic en **Agregar referencia**.

2. En el cuadro de diálogo **Agregar referencia** , seleccione los ensamblados o proyectos y, a continuación, haga clic en **Aceptar**.

## <a name="validate-code-manually"></a>Validar código manualmente

Si tiene un diagrama de dependencias abierto que está vinculado a elementos de la solución, puede ejecutar el comando **validar** acceso directo desde el diagrama. También puede usar el símbolo del sistema para ejecutar el comando **msbuild** con la propiedad personalizada **/p: pValidateArchitecture** establecida en **true**. Por ejemplo, cuando haga cambios en el código, realice la validación de capas con regularidad para detectar pronto los conflictos de dependencia.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Validar código desde un diagrama de dependencias abierto

1. Haga clic con el botón secundario en la superficie del diagrama y, a continuación, haga clic en **validar arquitectura**.

    > [!NOTE]
    > De forma predeterminada, la propiedad **acción de compilación** en el archivo de diagrama de dependencias (. layerdiagram) se establece en **Validate** para que el diagrama se incluya en el proceso de validación.

     La ventana **lista de errores** informa de los errores que se producen. Para obtener más información sobre los errores de validación, vea [solucionar problemas de validación de capas](#troubleshoot-layer-validation-issues).

2. Para ver el origen de cada error, haga doble clic en el error en la ventana **lista de errores** .

    > [!NOTE]
    > Visual Studio podría mostrar un mapa de código en lugar del origen del error. Esto se produce cuando el código tiene una dependencia en un ensamblado que no se especifica en el diagrama de dependencia o cuando el código no tiene una dependencia especificada por el diagrama de dependencia. Revise el mapa de código o el código para determinar si debe existir la dependencia. Para obtener más información sobre los mapas de código, vea [asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md).

3. Para administrar los errores, vea [resolver errores de validación de capas](#resolve-layer-validation-errors).

### <a name="validate-code-at-the-command-prompt"></a>Validar el código en el símbolo del sistema

1. Abra el símbolo del sistema de Visual Studio.

2. Elija una de las siguientes opciones:

   - Para validar el código con respecto a un proyecto de modelado específico en la solución, ejecute MSBuild con la siguiente propiedad personalizada.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - O

       Vaya a la carpeta que contiene el archivo de proyecto de modelado (. modelproj) y el diagrama de dependencia y, a continuación, ejecute MSBuild con la siguiente propiedad personalizada:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Para validar el código en todos los proyectos de modelado de la solución, ejecute MSBuild con la siguiente propiedad personalizada:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - O

       Vaya a la carpeta de la solución, que debe contener un proyecto de modelado que contenga un diagrama de dependencia y, a continuación, ejecute MSBuild con la siguiente propiedad personalizada:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Se mostrará cualquier error que se produzca. Para obtener más información acerca de MSBuild, vea [msbuild](../msbuild/msbuild.md) y [msbuild (tarea](../msbuild/msbuild-task.md)).

   Para obtener más información sobre los errores de validación, vea [solucionar problemas de validación de capas](#troubleshoot-layer-validation-issues).

### <a name="manage-validation-errors"></a>Administrar errores de validación

Durante el proceso de desarrollo, puede que desee suprimir algunos de los conflictos notificados durante la validación. Por ejemplo, es posible que desee suprimir errores de los que ya se ha ocupado o que no son pertinentes para su escenario concreto. Cuando se suprime un error, se recomienda registrar un elemento de trabajo en Team Foundation.

> [!WARNING]
> Ya debe estar conectado al control de código fuente TFS (SCC) para crear o vincular a un elemento de trabajo. Si intenta abrir una conexión a un SCC TFS diferente, Visual Studio cierra automáticamente la solución actual. Asegúrese de que ya está conectado al SCC apropiado antes de intentar crear o vincular a un elemento de trabajo. En las versiones posteriores de Visual Studio, los comandos de menú no están disponibles si no está conectado a un SCC.

#### <a name="create-a-work-item-for-a-validation-error"></a>Crear un elemento de trabajo para un error de validación

- En la ventana de **lista de errores** , haga clic con el botón secundario en el error, seleccione **crear elemento de trabajo**y, a continuación, haga clic en el tipo de elemento de trabajo que desea crear.

Use estas tareas para administrar los errores de validación en la ventana de **lista de errores** :

|**En**|**Siga estos pasos**|
|-|-|
|Suprimir los errores seleccionados durante la validación|Haga clic con el botón secundario en uno o varios errores seleccionados, seleccione **administrar errores de validación**y, a continuación, haga clic en **suprimir errores**.<br /><br /> Los errores suprimidos aparecen tachados. La próxima vez que ejecute la validación, estos errores no aparecerán.<br /><br /> Se realiza un seguimiento de los errores suprimidos en un archivo. resuppresss para el archivo de diagrama de dependencia correspondiente.|
|Detener la supresión de los errores seleccionados|Haga clic con el botón secundario en el error o errores suprimidos seleccionados, elija **administrar errores de validación**y, a continuación, haga clic en **detener la supresión de errores**.<br /><br /> La próxima vez que ejecute la validación, los errores suprimidos aparecerán.|
|Restaurar todos los errores suprimidos en la ventana de **lista de errores**|Haga clic con el botón secundario en cualquier lugar de la ventana de **lista de errores** , seleccione **administrar errores de validación**y, a continuación, haga clic en **Mostrar todos los errores suprimidos**.|
|Ocultar todos los errores suprimidos en la ventana de **lista de errores**|Haga clic con el botón secundario en cualquier lugar de la ventana de **lista de errores** , seleccione **administrar errores de validación**y, a continuación, haga clic en **ocultar todos los errores suprimidos**.|

## <a name="validate-code-automatically"></a>Validar código automáticamente

Puede realizar la validación de capas cada vez que ejecute una compilación local. Si el equipo usa Azure DevOps, puede realizar la validación de capas con protecciones controladas, que puede especificar creando una tarea MSBuild personalizada, y usar informes de compilación para recopilar los errores de validación. Para crear compilaciones de protección controlada, consulte [inserción en el repositorio validada de TFVC](/azure/devops/pipelines/build/triggers#gated).

### <a name="to-validate-code-automatically-during-a-local-build"></a>Para validar código automáticamente durante una compilación local

Use un editor de texto para abrir el archivo del proyecto de modelado (.modelproj) y, a continuación, incluya la siguiente propiedad:

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- o -

1. En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto de modelado que contiene el diagrama o diagramas de dependencia y, a continuación, haga clic en **propiedades**.

2. En la ventana **propiedades** , establezca la propiedad **validar arquitectura** del proyecto de modelado en **true**.

    Esto incluye el proyecto de modelado en el proceso de validación.

3. En **Explorador de soluciones**, haga clic en el archivo de diagrama de dependencias (. layerdiagram) que desee usar para la validación.

4. En la ventana **propiedades** , asegúrese de que la propiedad **acción de compilación** del diagrama está establecida en **validar**.

    Esto incluye el diagrama de dependencia en el proceso de validación.

Para administrar los errores en la ventana de Lista de errores, vea [resolver errores de validación de capas](#resolve-layer-validation-errors).

## <a name="troubleshoot-layer-validation-issues"></a>Solucionar problemas de validación de capas

En la siguiente tabla se describen problemas de validación de capas y su resolución. Estos problemas difieren de los errores que son resultado de conflictos entre el código y el diseño. Para obtener más información sobre estos errores, vea [solucionar problemas de validación de capas](#troubleshoot-layer-validation-issues).

|**Problema**|**Causa posible**|**Resolución**|
|-|-|-|
|Los errores de validación no se producen como se espera.|La validación no funciona en diagramas de dependencia que se copian desde otros diagramas de dependencia en Explorador de soluciones y que se encuentran en el mismo proyecto de modelado. los diagramas de dependencia que se copian de esta manera contienen las mismas referencias que el diagrama de dependencias original.|Agregue un nuevo diagrama de dependencia al proyecto de modelado.<br /><br /> Copie los elementos del diagrama de dependencias de origen en el nuevo diagrama.|

## <a name="resolve-layer-validation-errors"></a>Resolver errores de validación de capas

Al validar el código con un diagrama de dependencia, se producen errores de validación cuando el código entra en conflicto con el diseño. Por ejemplo, las siguientes condiciones podrían producir errores de validación:

- Un artefacto se ha asignado a la capa equivocada. En este caso, mueva el artefacto.

- Un artefacto, como por ejemplo una clase, usa otra clase de forma que hay conflictos con su arquitectura. En este caso, tiene que refactorizar el código para quitar la dependencia.

Para resolver estos errores, actualice el código hasta no aparezcan más errores durante la validación. Puede realizar esta tarea repetitivamente.

En la sección siguiente se describe la sintaxis que se usa en estos errores, se explica el significado de los mismos y se sugiere qué se puede hacer para resolverlos o administrarlos.

|**Sintaxis**|**Descripción**|
|-|-|
|*Artefacton*(*ArtifactTypeN*)|*Artefacton* es un artefacto que está asociado a una capa del diagrama de dependencia.<br /><br /> *ArtifactTypeN* es el tipo de *artefacton*, como una **clase** o un **método**, por ejemplo:<br /><br /> MiSolución.MiProyecto.MiClase.MiMétodo(Método)|
|*NamespaceNameN*|Nombre de un espacio de nombres.|
|*LayerNameN*|El nombre de una capa en el diagrama de dependencia.|
|*DependencyType*|El tipo de relación de dependencia entre *artefacto 1* y *artefacto 2*. Por ejemplo, *artefacto 1* tiene una relación de **llamadas** con *artefacto 2*.|

| **Sintaxis de error** | **Descripción del error** |
|-|-|
| DV0001: **dependencia no válida** | Este problema se produce cuando un elemento de código (espacio de nombres, tipo, miembro) asignado a una capa hace referencia a un elemento de código asignado a otra capa, pero no hay ninguna flecha de dependencia entre estas capas en el diagrama de validación de dependencias que contiene estas capas. Se trata de una infracción de restricción de dependencia. |
| DV1001: **nombre de espacio de nombres no válido** | Este problema se indica en un elemento de código asociado a una capa que la propiedad "nombres de espacios de nombres permitidos" no contiene el espacio de nombres en el que se define este elemento de código. Se trata de una infracción de la restricción de nomenclatura. Tenga en cuenta que la sintaxis de "nombres de espacios de nombres permitidos" es una lista de espacios de nombres de punto y coma en la que se permite definir elementos de código asociados con. |
| DV1002: **dependencia en un espacio de nombres sin referencia** | Este problema se indica en un elemento de código asociado a una capa y que hace referencia a otro elemento de código definido en un espacio de nombres que se define en la propiedad "espacio de nombres sin referencia" de la capa. Se trata de una infracción de la restricción de nomenclatura. Tenga en cuenta que la propiedad "espacios de nombres sin referencias" se define como una lista separada por punto y coma de los espacios de nombres a los que no se debe hacer referencia en los elementos de código asociados a esta capa. |
| DV1003: **nombre de espacio de nombres no permitido** | Este problema se indica en un elemento de código asociado a una capa que contiene la propiedad "nombres de espacios de nombres no permitidos" que contiene el espacio de nombres en el que está definido este elemento de código. Se trata de una infracción de la restricción de nomenclatura. Tenga en cuenta que la propiedad "nombre de espacio de nombres no permitido" se define como una lista de espacios de nombres separados por punto y coma en la que no se deben definir los elementos de código asociados a esta capa. |
| DV3001: **falta un vínculo** | La capa '*LayerName*' está vinculada a '*artefacto*' que no se encuentra. ¿Falta una referencia de ensamblado? |
| DV9001: el **análisis arquitectónico encontró errores internos** | Puede que los resultados no estén completos. Vea el registro detallado de eventos de compilación o la ventana de salida para obtener más información. |

## <a name="see-also"></a>Vea también

- [Validación de dependencias dinámicas en Visual Studio](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [Validar el sistema durante el desarrollo](../modeling/validate-your-system-during-development.md)
- [Vídeo: validar las dependencias de la arquitectura en tiempo real](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
