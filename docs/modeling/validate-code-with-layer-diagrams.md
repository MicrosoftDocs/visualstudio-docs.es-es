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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: fd4e3681ad30dc54d9240fff94e1bf60bf5e88cf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55033952"
---
# <a name="validate-code-with-dependency-diagrams"></a>Validación código con diagramas de dependencia

## <a name="why-use-dependency-diagrams"></a>¿Por qué usar diagramas de dependencia?

Para asegurarse de que código no entre en conflicto con el diseño, valide el código con diagramas de dependencia en Visual Studio. Esto puede ser útil para:

- Busque los conflictos entre dependencias en el código y dependencias en el diagrama de dependencia.

- Encontrar dependencias que podrían verse afectadas por los cambios propuestos.

   Por ejemplo, puede editar el diagrama de dependencia para mostrar los posibles cambios de arquitectura y, a continuación, validar el código para ver las dependencias afectadas.

- Refactorizar o migrar el código a un diseño diferente.

   Encontrar código o dependencias que requieran trabajo al cambiar el código a una arquitectura diferente.

**Requisitos**

- Programa para la mejora

- Una solución que tiene un proyecto de modelado con un diagrama de dependencia. Este diagrama de dependencia debe vincularse a artefactos de proyectos de C# o Visual Basic que se desean validar. Consulte [crear diagramas de dependencia desde el código](../modeling/create-layer-diagrams-from-your-code.md).

> [!NOTE]
> Diagramas de dependencia no se admiten para los proyectos de .NET Core en Visual Studio 2017.

Para ver qué ediciones de Visual Studio admiten esta característica, vea [compatibilidad con la edición de arquitectura y las herramientas de modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Puede validar código manualmente desde un diagrama de dependencia abierto en Visual Studio o desde un símbolo del sistema. También puede validar código automáticamente cuando se ejecutan compilaciones locales o canalizaciones de Azure compilaciones. Consulte [vídeo de Channel 9: Diseñar y validar la arquitectura mediante diagramas de dependencia](http://go.microsoft.com/fwlink/?LinkID=252073).

> [!IMPORTANT]
> Si desea ejecutar la validación de capa con Team Foundation Server (TFS), también debe instalar la misma versión de Visual Studio en el servidor de compilación.

## <a name="live-dependency-validation"></a>Validación de dependencias en vivo

Se produce la validación de dependencias en tiempo real y los errores se muestran inmediatamente en el **lista de errores**.

* Se admite la validación en vivo para C# y Visual Basic.

* Para habilitar el análisis de la solución completa cuando se usa la validación de dependencias en vivo, abra las opciones de configuración de la barra dorada que aparece en el **lista de errores**.

   - Puede descartar la barra dorada permanentemente si no está interesado en ver todos los problemas de arquitectura de la solución.
   - Si no habilita el análisis de la solución completa, el análisis se realiza solo para los archivos que se está editando.

* Al actualizar los proyectos para habilitar la validación en vivo, un cuadro de diálogo muestra el progreso de la conversión.

* Al actualizar un proyecto de validación de dependencias en vivo, la versión del paquete NuGet se actualiza para que sea el mismo para todos los proyectos y es la versión más alta en uso.

* Agregar un nuevo desencadenadores de proyecto de validación de dependencia de una actualización del proyecto.

## <a name="see-if-an-item-supports-validation"></a>Ver si un elemento admite validación

Puede vincular capas a sitios Web, documentos de Office, archivos de texto sin formato y archivos de proyectos que se comparten entre varias aplicaciones, pero el proceso de validación no los incluirá. Los errores de validación no aparecerán para las referencias a proyectos o ensamblados que están vinculados a capas independientes cuando no aparece ninguna dependencia entre esas capas. Tales referencias no se consideran dependencias a menos que el código utilice esas referencias.

1.  En el diagrama de dependencia, seleccione una o varias capas, haga clic en la selección y, a continuación, haga clic en **ver vínculos**.

2.  En **Explorador de capas**, examine el **admite validación** columna. Si el valor es false, el elemento no admite la validación.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Incluir otros ensamblados y proyectos de .NET para su validación

Al arrastrar elementos al diagrama de dependencia, las referencias a los ensamblados de .NET correspondientes o proyectos se agregan automáticamente a la **referencias de capa** carpeta en el proyecto de modelado. Esta carpeta contiene referencias a los ensamblados y proyectos que se analizan durante la validación. Puede incluir otros ensamblados .NET y proyectos para la validación sin arrastrarlos manualmente al diagrama de dependencia.

1.  En **el Explorador de soluciones**, haga clic en el proyecto de modelado o **referencias de capa** carpeta y, a continuación, haga clic en **Agregar referencia**.

2.  En el **Agregar referencia** cuadro de diálogo, seleccione los ensamblados o proyectos y, a continuación, haga clic en **Aceptar**.

## <a name="validate-code-manually"></a>Validar código manualmente

Si tiene un diagrama abierto de dependencia que esté vinculado a elementos de la solución, puede ejecutar el **validar** comando de acceso directo del diagrama. También puede usar la línea de comandos para ejecutar el **msbuild** comando con el **pValidateArchitecture** propiedad personalizada establecida en **True**. Por ejemplo, cuando haga cambios en el código, realice la validación de capas con regularidad para detectar pronto los conflictos de dependencia.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Validar el código de un diagrama de dependencia abierto

1.  Haga clic en la superficie del diagrama y, a continuación, haga clic en **validar arquitectura**.

    > [!NOTE]
    > De forma predeterminada, el **acción de compilación** propiedad en el archivo de diagrama (.layerdiagram) de dependencia se establece en **validar** para que el diagrama se incluye en el proceso de validación.

     El **lista de errores** ventana notifica los errores que se producen. Para obtener más información sobre los errores de validación, consulte [entender y resolver errores de validación de capas](#UnderstandingValidationErrors).

2.  Para ver el origen de cada error, haga doble clic en el error en la **lista de errores** ventana.

    > [!NOTE]
    > Visual Studio podría mostrar un mapa de código en lugar del origen del error. Esto se produce cuando el código tiene una dependencia en un ensamblado que no se especifica en el diagrama de dependencia o el código le falta una dependencia que se especifica en el diagrama de dependencia. Revise el mapa de código o el código para determinar si debe existir la dependencia. Para obtener más información acerca de los mapas de código, vea [asignar dependencias en sus soluciones](../modeling/map-dependencies-across-your-solutions.md).

3.  Para administrar los errores, vea [administrar errores de validación](#ManageErrors).

### <a name="validate-code-at-the-command-prompt"></a>Validar el código en el símbolo del sistema

1. Abra el símbolo del sistema de Visual Studio.

2. Elija una de las siguientes opciones:

   - Para validar el código con un proyecto de modelado específicos de la solución, ejecute MSBuild con la siguiente propiedad personalizada.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - O

       Vaya a la carpeta que contiene el proyecto de modelado (.modelproj) archivo y la dependencia de diagrama y, a continuación, ejecutar MSBuild con la siguiente propiedad personalizada:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Para validar el código comparándolo con todos los proyectos de modelado en la solución, ejecute MSBuild con la siguiente propiedad personalizada:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - O

       Vaya a la carpeta de soluciones, que debe contener un proyecto de modelado que contiene un diagrama de dependencia y, a continuación, ejecutar MSBuild con la siguiente propiedad personalizada:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Se mostrará cualquier error que se produzca. Para obtener más información acerca de MSBuild, vea [MSBuild](../msbuild/msbuild.md) y [tarea MSBuild](../msbuild/msbuild-task.md).

   Para obtener más información sobre los errores de validación, consulte [entender y resolver errores de validación de capas](#UnderstandingValidationErrors).

### <a name="manage-validation-errors"></a>Administrar errores de validación

Durante el proceso de desarrollo, puede que desee suprimir algunos de los conflictos notificados durante la validación. Por ejemplo, es posible que desee suprimir errores de los que ya se ha ocupado o que no son pertinentes para su escenario concreto. Cuando se suprime un error, es una buena práctica para registrar un elemento de trabajo en Team Foundation.

> [!WARNING]
> Ya debe estar conectado al control de código fuente TFS (SCC) para crear o vincular a un elemento de trabajo. Si intenta abrir una conexión a un SCC TFS diferente, Visual Studio cierra automáticamente la solución actual. Asegúrese de que ya está conectado al SCC apropiado antes de intentar crear o vincular a un elemento de trabajo. En las versiones posteriores de Visual Studio, los comandos de menú no están disponibles si no está conectado a un SCC.

#### <a name="create-a-work-item-for-a-validation-error"></a>Crear un elemento de trabajo para un error de validación

- En el **lista de errores** ventana, haga clic en el error, seleccione **crear elemento de trabajo**y, a continuación, haga clic en el tipo de elemento de trabajo que desea crear.

Utilice estos procedimientos para administrar errores de validación en el **lista de errores** ventana:

|**En**|**Siga estos pasos**|
|-|-|
|Suprimir los errores seleccionados durante la validación|Haga clic en el uno o varios errores seleccionados, elija **administrar errores de validación**y, a continuación, haga clic en **suprimir errores**.<br /><br /> Los errores suprimidos aparecen tachados. La próxima vez que ejecute la validación, estos errores no aparecerán.<br /><br /> Errores suprimidos se realiza un seguimiento en un archivo .suppressions relacionado con el archivo de diagrama de dependencia correspondiente.|
|Detener la supresión de los errores seleccionados|Haga clic en los errores suprimidos seleccionados o errores, seleccione **administrar errores de validación**y, a continuación, haga clic en **Detener supresión de errores**.<br /><br /> La próxima vez que ejecute la validación, los errores suprimidos aparecerán.|
|Restaurar todos los errores suprimidos en la **lista de errores** ventana|Haga clic en cualquier lugar en el **lista de errores** ventana, seleccione **administrar errores de validación**y, a continuación, haga clic en **mostrar errores suprimidos**.|
|Ocultar todos los errores suprimidos desde el **lista de errores** ventana|Haga clic en cualquier lugar en el **lista de errores** ventana, seleccione **administrar errores de validación**y, a continuación, haga clic en **Ocultar errores suprimidos**.|

## <a name="validate-code-automatically"></a>Validar código automáticamente

Puede realizar la validación de capas cada vez que ejecute una compilación local. Si el equipo usa DevOps de Azure, puede realizar la validación de capas con protecciones controladas, que se pueden especificar mediante la creación de una tarea MSBuild personalizada y usar informes de compilación para recopilar errores de validación. Para crear compilaciones de protección controladas, consulte [TFVC validada](/azure/devops/pipelines/build/triggers#gated).

### <a name="to-validate-code-automatically-during-a-local-build"></a>Para validar código automáticamente durante una compilación local

Use un editor de texto para abrir el archivo del proyecto de modelado (.modelproj) y, a continuación, incluya la siguiente propiedad:

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- o -

1.  En **el Explorador de soluciones**, haga clic en el proyecto de modelado que contiene el diagrama de dependencias o diagramas y, a continuación, haga clic en **propiedades**.

2.  En el **propiedades** ventana, establezca el proyecto de modelado **validar arquitectura** propiedad **True**.

    Esto incluye el proyecto de modelado en el proceso de validación.

3.  En **el Explorador de soluciones**, haga clic en el archivo de diagrama (.layerdiagram) de dependencia que se desea utilizar para la validación.

4.  En el **propiedades** ventana, asegúrese de que el diagrama **acción de compilación** propiedad está establecida en **validar**.

    Esto incluye el diagrama de dependencia en el proceso de validación.

Para administrar los errores en la ventana Lista de errores, vea [administrar errores de validación](#ManageErrors).

## <a name="troubleshoot-layer-validation-issues"></a>Solucionar problemas de validación de capas

En la siguiente tabla se describen problemas de validación de capas y su solución. Estos problemas difieren de los errores que son resultado de conflictos entre el código y el diseño. Para obtener más información acerca de estos errores, vea [entender y resolver errores de validación de capas](#UnderstandingValidationErrors).

|**Problema**|**Causa posible**|**Resolución**|
|-|-|-|
|Los errores de validación no se producen como se espera.|La validación no funciona en los diagramas de dependencia que se copian de otros diagramas de dependencia en el Explorador de soluciones y que están en el mismo proyecto de modelado. diagramas de dependencia que se copian de esta manera contienen las mismas referencias que el diagrama de dependencia original.|Agregue un nuevo diagrama de dependencia al proyecto de modelado.<br /><br /> Copiar los elementos del diagrama de dependencia de origen en el nuevo diagrama.|

## <a name="resolve-layer-validation-errors"></a>Resolver errores de validación de capas

Cuando se valida el código con un diagrama de dependencia, se producen errores de validación cuando el código entra en conflicto con el diseño. Por ejemplo, las siguientes condiciones podrían producir errores de validación:

- Un artefacto se ha asignado a la capa equivocada. En este caso, mueva el artefacto.

- Un artefacto, como por ejemplo una clase, usa otra clase de forma que hay conflictos con su arquitectura. En este caso, tiene que refactorizar el código para quitar la dependencia.

Para resolver estos errores, actualice el código hasta no aparezcan más errores durante la validación. Puede realizar esta tarea repetitivamente.

En la sección siguiente se describe la sintaxis que se usa en estos errores, se explica el significado de los mismos y se sugiere qué se puede hacer para resolverlos o administrarlos.

|**Sintaxis**|**Descripción**|
|-|-|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* es un artefacto que está asociado a una capa en el diagrama de dependencia.<br /><br /> *ArtifactTypeN* es el tipo de *ArtifactN*, como un **clase** o **método**, por ejemplo:<br /><br /> MiSolución.MiProyecto.MiClase.MiMétodo(Método)|
|*NamespaceNameN*|Nombre de un espacio de nombres.|
|*LayerNameN*|El nombre de una capa en el diagrama de dependencia.|
|*DependencyType*|El tipo de relación de dependencia entre *Artifact1* y *Artifact2*. Por ejemplo, *Artifact1* tiene un **llamadas** relación con *Artifact2*.|

| **Error de sintaxis** | **Descripción del error** |
|-|-|
| DV0001: **Dependencia no válida** | Este problema se notifica cuando un elemento de código (espacio de nombres, tipo, miembro) asignado a referencias de una capa de un elemento de código asignado a otra capa, pero no hay ninguna flecha de dependencia entre estas capas en el diagrama de validación de dependencia que contiene este capas. Se trata de una infracción de restricción de dependencia. |
| DV1001: **Nombre del espacio de nombres no válido** | Este problema se notifica en un elemento de código asociado a una capa que "Permite nombres de Namespace" propiedad no contienen el espacio de nombres en el que se define este elemento de código. Se trata de una infracción de restricción de nomenclatura. Tenga en cuenta que la sintaxis de "Permite nombres de Namespace" sea una lista de puntos y coma de los espacios de nombres en el código que los elementos asociados son capa pueden definirse. |
| DV1002: **Dependencia de espacio de nombres a** | Este problema se notifica en un elemento de código asociado a una capa y hacer referencia a otro elemento de código definido en un espacio de nombres que se define en la propiedad "Namespace a" de la capa. Se trata de una infracción de restricción de nomenclatura. Tenga en cuenta que la propiedad "Espacios de nombres a" se define como una lista separada por punto y coma de los espacios de nombres que no se deben hacer referencia en los elementos de código asociados a esta capa. |
| DV1003: **Nombre del espacio de nombres no permitidos** | Este problema se notifica en un elemento de código asociado con una capa de propiedad de "No permite nombres de Namespace" contiene el espacio de nombres en el que se define este elemento de código. Se trata de una infracción de restricción de nomenclatura. Tenga en cuenta que la propiedad "Nombre del espacio de nombres no permitido" se define como una lista separada por punto y coma de los espacios de nombres en el código que no se deben definir los elementos asociados a esta capa. |
| DV3001: **Vínculo que falta** | Capa '*LayerName*'vincula a'*artefacto*' que no se encuentra. ¿Falta una referencia de ensamblado? |
| DV9001: **Análisis de arquitectura encontró errores internos** | Puede que los resultados no estén completos. Vea el registro detallado de eventos de compilación o la ventana de salida para obtener más información. |

## <a name="see-also"></a>Vea también

- [Validación dinámica de dependencias en Visual Studio 2017](https://blogs.msdn.microsoft.com/devops/2016/11/30/live-dependency-validation-in-visual-studio-2017/)
- [Validar el sistema durante el desarrollo](../modeling/validate-your-system-during-development.md)
- [Vídeo: Validar las dependencias de arquitectura en tiempo real](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)