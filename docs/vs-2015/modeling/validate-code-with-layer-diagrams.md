---
title: Validar el código con diagramas de capas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, validating
- validation, layer diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, layer diagrams
- MSBuild, validating code
ms.assetid: 70cbe55d-4b33-4355-b0a7-88c770a6f75c
caps.latest.revision: 84
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 596711c5c59738d5356437bb761e80caeddfbd6b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301358"
---
# <a name="validate-code-with-layer-diagrams"></a>Validar código con diagramas de capas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para asegurarse de que el código no entre en conflicto con el diseño, puede validarlo con diagramas de capas en Visual Studio. Esto puede ser útil para:

- Encontrar los conflictos entre las dependencias del código y las dependencias del diagrama de capas.

- Encontrar dependencias que podrían verse afectadas por los cambios propuestos.

   Por ejemplo, puede modificar el diagrama de capas para mostrar los posibles cambios de la arquitectura y validar el código para ver las dependencias afectadas.

- Refactorizar o migrar el código a un diseño diferente.

   Encontrar código o dependencias que requieran trabajo al cambiar el código a una arquitectura diferente.

  **Requisitos**

- Visual Studio

- Visual Studio en el servidor de Team Foundation Build para validar código automáticamente con Team Foundation Build

- Una solución que tenga un proyecto de modelado con un diagrama de capas. Este diagrama de capas debe vincularse a artefactos de proyectos de Visual C# .NET o Visual Basic .NET que desea validar. Vea [crear diagramas de capas desde el código](../modeling/create-layer-diagrams-from-your-code.md).

  Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

  Puede validar código manualmente desde un diagrama de capas abierto en Visual Studio o desde un símbolo del sistema. También puede validar código automáticamente al ejecutar compilaciones locales o Team Foundation Build. Consulte [vídeo de Channel 9: diseñar y validar la arquitectura mediante diagramas de capas](https://go.microsoft.com/fwlink/?LinkID=252073).

> [!IMPORTANT]
> Si desea ejecutar la validación de capa con Team Foundation Build, debe instalar también la misma versión de Visual Studio en el servidor de compilación.

- [Ver si un elemento admite la validación](#SupportsValidation)

- [Incluir otros ensamblados .NET y proyectos para la validación](#IncludeReferences)

- [Validar código manualmente](#ValidateManually)

- [Validar código automáticamente](#ValidateAuto)

- [Solucionar problemas de validación de capas](#TroubleshootingValidation)

- [Comprender y resolver errores de validación de capas](#UnderstandingValidationErrors)

## <a name="SupportsValidation"></a>Ver si un elemento admite la validación
 Puede vincular capas a sitios web, documentos de Office, archivos de texto sin formato y archivos de proyectos que se comparten entre varias aplicaciones, pero el proceso de validación no los incluirá. Los errores de validación no aparecerán para las referencias a proyectos o ensamblados que están vinculados a capas independientes cuando no aparece ninguna dependencia entre esas capas. Tales referencias no se consideran dependencias a menos que el código utilice esas referencias.

1. En el diagrama de capas, seleccione una o varias capas, haga clic con el botón secundario en la selección y, a continuación, haga clic en **ver vínculos**.

2. En el **Explorador de capas**, examine la columna **admite validación** . Si el valor es false, el elemento no admite la validación.

## <a name="IncludeReferences"></a>Incluir otros ensamblados .NET y proyectos para la validación
 Al arrastrar elementos al diagrama de capas, las referencias a los ensamblados o proyectos .NET correspondientes se agregan automáticamente a la carpeta **referencias de capa** del proyecto de modelado. Esta carpeta contiene referencias a los ensamblados y proyectos que se analizan durante la validación. Puede incluir otros ensamblados y proyectos de .NET para validación sin arrastrarlos manualmente al diagrama de capas.

1. En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto de modelado o en la carpeta **referencias de capa** y, a continuación, haga clic en **Agregar referencia**.

2. En el cuadro de diálogo **Agregar referencia** , seleccione los ensamblados o proyectos y, a continuación, haga clic en **Aceptar**.

## <a name="ValidateManually"></a>Validar código manualmente
 Si tiene un diagrama de capas abierto que está vinculado a elementos de la solución, puede ejecutar el comando **validar** acceso directo desde el diagrama. También puede usar el símbolo del sistema para ejecutar el comando **msbuild** con la propiedad personalizada **/p: pValidateArchitecture** establecida en **true**. Por ejemplo, cuando haga cambios en el código, realice la validación de capas con regularidad para detectar pronto los conflictos de dependencia.

#### <a name="to-validate-code-from-an-open-layer-diagram"></a>Para validar el código de un diagrama de capas abierto

1. Haga clic con el botón secundario en la superficie del diagrama y, a continuación, haga clic en **validar arquitectura**.

    > [!NOTE]
    > De forma predeterminada, la propiedad **acción de compilación** en el archivo de diagrama de capas (. layerdiagram) se establece en **Validate** para que el diagrama se incluya en el proceso de validación.

     La ventana **lista de errores** informa de los errores que se producen. Para obtener más información sobre los errores de validación, vea [comprender y resolver errores de validación de capas](#UnderstandingValidationErrors).

2. Para ver el origen de cada error, haga doble clic en el error en la ventana **lista de errores** .

    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] podría mostrar un mapa de código en lugar del origen del error. Esto se produce cuando el código tiene una dependencia en un ensamblado que el diagrama de capas no especifica, o al código le falta una dependencia que el diagrama de capas especifica. Revise el mapa de código o el código para determinar si debe existir la dependencia. Para obtener más información sobre los mapas de código, vea [asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md).

3. Para administrar los errores, consulte [administrar errores de validación](#ManageErrors).

#### <a name="to-validate-code-at-the-command-prompt"></a>Para validar código en el símbolo del sistema

1. Abra el símbolo del sistema de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

2. Elija una de las siguientes opciones:

   - Para validar el código comparándolo con un proyecto de modelado concreto en la solución, ejecute [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] con la siguiente propiedad personalizada.

     ```
     msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
     ```

     - O

       Vaya a la carpeta que contiene el archivo de proyecto de modelado (.modelproj) y el diagrama de capas y, a continuación, ejecute [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] con la siguiente propiedad personalizada:

     ```
     msbuild /p:ValidateArchitecture=true
     ```

   - Para validar el código comparándolo con todos los proyectos de modelado de la solución, ejecute [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] con la siguiente propiedad personalizada.

     ```
     msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
     ```

     - O

       Vaya a la carpeta de soluciones, que debe contener un proyecto de modelado que contiene un diagrama de capas y, a continuación, ejecute [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] con la siguiente propiedad personalizada:

     ```
     msbuild /p:ValidateArchitecture=true
     ```

     Se mostrará cualquier error que se produzca. Para obtener más información acerca de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], vea [msbuild](../msbuild/msbuild.md) y [msbuild (tarea](../msbuild/msbuild-task.md)).

   Para obtener más información sobre los errores de validación, vea [comprender y resolver errores de validación de capas](#UnderstandingValidationErrors).

### <a name="ManageErrors"></a>Administrar errores de validación
 Durante el proceso de desarrollo, puede que desee suprimir algunos de los conflictos notificados durante la validación. Por ejemplo, es posible que desee suprimir errores de los que ya se ha ocupado o que no son pertinentes para su escenario concreto. Cuando se suprime un error, conviene registrar un elemento de trabajo en [!INCLUDE[esprfound](../includes/esprfound-md.md)].

> [!WARNING]
> Ya debe estar conectado al control de código fuente TFS (SCC) para crear o vincular a un elemento de trabajo. Si intenta abrir una conexión a un SCC TFS diferente, Visual Studio cierra automáticamente la solución actual. Asegúrese de que ya está conectado al SCC apropiado antes de intentar crear o vincular a un elemento de trabajo. En las versiones posteriores de Visual Studio, los comandos de menú no están disponibles si no está conectado a un SCC.

##### <a name="to-create-a-work-item-for-a-validation-error"></a>Para crear un elemento de trabajo para un error de validación

- En la ventana de **lista de errores** , haga clic con el botón secundario en el error, seleccione **crear elemento de trabajo**y, a continuación, haga clic en el tipo de elemento de trabajo que desea crear.

  Use estas tareas para administrar los errores de validación en la ventana de **lista de errores** :

|**En**|**Siga estos pasos**|
|------------|----------------------------|
|Suprimir los errores seleccionados durante la validación|Haga clic con el botón secundario en uno o varios errores seleccionados, seleccione **administrar errores de validación**y, a continuación, haga clic en **suprimir errores**.<br /><br /> Los errores suprimidos aparecen tachados. La próxima vez que ejecute la validación, estos errores no aparecerán.<br /><br /> El seguimiento de los errores suprimidos se lleva a cabo en un archivo .suppressions relacionado con el archivo de diagrama de capas correspondiente.|
|Detener la supresión de los errores seleccionados|Haga clic con el botón secundario en el error o errores suprimidos seleccionados, elija **administrar errores de validación**y, a continuación, haga clic en **detener la supresión de errores**.<br /><br /> La próxima vez que ejecute la validación, los errores suprimidos aparecerán.|
|Restaurar todos los errores suprimidos en la ventana de **lista de errores**|Haga clic con el botón secundario en cualquier lugar de la ventana de **lista de errores** , seleccione **administrar errores de validación**y, a continuación, haga clic en **Mostrar todos los errores suprimidos**.|
|Ocultar todos los errores suprimidos en la ventana de **lista de errores**|Haga clic con el botón secundario en cualquier lugar de la ventana de **lista de errores** , seleccione **administrar errores de validación**y, a continuación, haga clic en **ocultar todos los errores suprimidos**.|

## <a name="ValidateAuto"></a>Validar código automáticamente
 Puede realizar la validación de capas cada vez que ejecute una compilación local. Si el equipo usa Team Foundation Build, podrá realizar la validación de capas con inserciones en el repositorio validadas, que se pueden especificar creando una tarea MSBuild personalizada, y usar informes de compilación para recopilar los errores de validación. Para crear compilaciones de protección controlada, consulte [usar un proceso de compilación de inserción en](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)el repositorio validada para validar cambios.

#### <a name="to-validate-code-automatically-during-a-local-build"></a>Para validar código automáticamente durante una compilación local

- Use un editor de texto para abrir el archivo del proyecto de modelado (.modelproj) y, a continuación, incluya la siguiente propiedad:

```
<ValidateArchitecture>true</ValidateArchitecture>
```

 \- o -

1. En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto de modelado que contiene los diagramas de capas y, a continuación, haga clic en **propiedades**.

2. En la ventana **propiedades** , establezca la propiedad **validar arquitectura** del proyecto de modelado en **true**.

    Esto incluye el proyecto de modelado en el proceso de validación.

3. En **Explorador de soluciones**, haga clic en el archivo de diagrama de capas (. layerdiagram) que desee usar para la validación.

4. En la ventana **propiedades** , asegúrese de que la propiedad **acción de compilación** del diagrama está establecida en **validar**.

    Esto incluye el diagrama de capas en el proceso de validación.

   Para administrar los errores en la ventana de Lista de errores, vea [administrar errores de validación](#ManageErrors).

#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>Para validar código automáticamente durante una compilación con Team Foundation Build

1. En **Team Explorer**, haga doble clic en la definición de compilación y, a continuación, haga clic en **procesar**.

2. En **parámetros del proceso de compilación**, expanda **compilación**y escriba lo siguiente en el parámetro **argumentos de MSBuild** :

    `/p:ValidateArchitecture=true`

   Para obtener más información sobre los errores de validación, vea [comprender y resolver errores de validación de capas](#UnderstandingValidationErrors). Para obtener más información acerca de [!INCLUDE[esprbuild](../includes/esprbuild-md.md)], vea:

- [Compilar la aplicación](/azure/devops/pipelines/index)

- [Usar la plantilla predeterminada para el proceso de compilación](https://msdn.microsoft.com/library/43930b12-c21b-4599-a980-2995e3d16e31)

- [Modificar una compilación heredada basada en UpgradeTemplate. Xaml](https://msdn.microsoft.com/library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)

- [Personalizar la plantilla de proceso de compilación](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

- [Supervisar el progreso de una compilación en ejecución](https://msdn.microsoft.com/library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)

## <a name="TroubleshootingValidation"></a>Solucionar problemas de validación de capas
 En la siguiente tabla se describen problemas de validación de capas y su resolución. Estos problemas difieren de los errores que son resultado de conflictos entre el código y el diseño. Para obtener más información sobre estos errores, consulte [entender y resolver errores de validación de capas](#UnderstandingValidationErrors).

|**Problema**|**Causa posible**|**Resolución**|
|---------------|------------------------|--------------------|
|Los errores de validación no se producen como se espera.|La validación no funciona en los diagramas de capas que se copian de otros diagramas de capas en el Explorador de soluciones y que están en el mismo proyecto de modelado. Los diagramas de capas que se copian de esta manera contienen las mismas referencias que el diagrama de capas original.|Agregue un nuevo diagrama de capas al proyecto de modelado.<br /><br /> Copie los elementos del diagrama de capas de origen en el nuevo diagrama.|

## <a name="UnderstandingValidationErrors"></a>Descripción y resolución de errores de validación de capas
 Cuando se valida el código con un diagrama de capas, se producen errores de validación si el código entra en conflicto con el diseño. Por ejemplo, las siguientes condiciones podrían producir errores de validación:

- Un artefacto se ha asignado a la capa equivocada. En este caso, mueva el artefacto.

- Un artefacto, como por ejemplo una clase, usa otra clase de forma que hay conflictos con su arquitectura. En este caso, tiene que refactorizar el código para quitar la dependencia.

  Para resolver estos errores, actualice el código hasta no aparezcan más errores durante la validación. Puede realizar esta tarea repetitivamente.

  En la sección siguiente se describe la sintaxis que se usa en estos errores, se explica el significado de los mismos y se sugiere qué se puede hacer para resolverlos o administrarlos.

|**Sintaxis**|**Descripción**|
|----------------|---------------------|
|*Artefacton*(*ArtifactTypeN*)|*Artefacton* es un artefacto que está asociado a una capa del diagrama de capas.<br /><br /> *ArtifactTypeN* es el tipo de *artefacton*, como una **clase** o un **método**, por ejemplo:<br /><br /> MiSolución.MiProyecto.MiClase.MiMétodo(Método)|
|*NamespaceNameN*|Nombre de un espacio de nombres.|
|*LayerNameN*|Nombre de una capa del diagrama de capas.|
|*DependencyType*|El tipo de relación de dependencia entre *artefacto 1* y *artefacto 2*. Por ejemplo, *artefacto 1* tiene una relación de **llamadas** con *artefacto 2*.|

|**Sintaxis de error**|**Descripción del error**|
|----------------------|---------------------------|
|AV0001: dependencia no válida: *artefacto 1*(*ArtifactType1*)--> *artefacto 2*(*ArtifactType2*)<br /><br /> Capas: *LayerName1*, *LayerName2* &#124; dependencies: *DependencyType*|*Artefacto 1* en *LayerName1* no debe tener una dependencia en *artefacto 2* en *LayerName2* porque *LayerName1* no tiene una dependencia directa en *LayerName2*.|
|AV1001: espacio de nombres no válido: *artefacto*<br /><br /> Capa: *LayerName* &#124; espacio de nombres necesario: *NamespaceName1* &#124; espacio de nombres actual: *NamespaceName2*|*LayerName* requiere que sus artefactos asociados pertenezcan a *NamespaceName1*. El *artefacto* está en *NamespaceName2*, no en *NamespaceName1*.|
|AV1002: depende de un espacio de nombres prohibido: *artefacto 1*(*ArtifactType1*) &#124; *artefacto 2*(*ArtifactType2*)<br /><br /> Capa: *LayerName* &#124; Forbidden namespace: *NamespaceName* &#124; dependencies: *DependencyType*|*LayerName* requiere que sus artefactos asociados no dependan de *NamespaceName*. *Artefacto 1* no puede depender de *artefacto 2* porque *artefacto 2* está en *NamespaceName*.|
|AV1003: en espacio de nombres prohibido: *artefacto*(*ArtifactType*)<br /><br /> Capa: *LayerName* &#124; prohibido espacio de nombres: *NamespaceName*|*LayerName* requiere que sus artefactos asociados no pertenezcan a *NamespaceName*. El *artefacto* pertenece a *NamespaceName*.|
|AV3001: falta un vínculo: la capa '*LayerName*' contiene vínculos a '*artefacto*' que no se encuentra. ¿Falta una referencia de ensamblado?|*LayerName* vincula a un artefacto que no se puede encontrar. Por ejemplo, es posible que falte un vínculo a una clase porque en el proyecto de modelado falta una referencia al ensamblado que contiene la clase.|
|AV9001: El análisis de arquitectura encontró errores internos. Puede que los resultados no estén completos. Vea el registro detallado de eventos de compilación o la ventana de salida para obtener más información.|Vea el registro de eventos de compilación o la ventana de salida para obtener más información.|

## <a name="security"></a>Seguridad

## <a name="see-also"></a>Vea también
 [Validar el sistema durante el desarrollo](../modeling/validate-your-system-during-development.md)
