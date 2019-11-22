---
title: Validate code with layer diagrams | Microsoft Docs
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

- Programa para la mejora

- Visual Studio en el servidor de Team Foundation Build para validar código automáticamente con Team Foundation Build

- Una solución que tenga un proyecto de modelado con un diagrama de capas. Este diagrama de capas debe vincularse a artefactos de proyectos de Visual C# .NET o Visual Basic .NET que desea validar. See [Create layer diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md).

  Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

  Puede validar código manualmente desde un diagrama de capas abierto en Visual Studio o desde un símbolo del sistema. También puede validar código automáticamente al ejecutar compilaciones locales o Team Foundation Build. See [Channel 9 Video: Design and validate your architecture using layer diagrams](https://go.microsoft.com/fwlink/?LinkID=252073).

> [!IMPORTANT]
> Si desea ejecutar la validación de capa con Team Foundation Build, debe instalar también la misma versión de Visual Studio en el servidor de compilación.

- [See if an item supports validation](#SupportsValidation)

- [Include other .NET assemblies and projects for validation](#IncludeReferences)

- [Validate code manually](#ValidateManually)

- [Validate code automatically](#ValidateAuto)

- [Troubleshoot layer validation issues](#TroubleshootingValidation)

- [Understand and resolve layer validation errors](#UnderstandingValidationErrors)

## <a name="SupportsValidation"></a> See if an item supports validation
 Puede vincular capas a sitios web, documentos de Office, archivos de texto sin formato y archivos de proyectos que se comparten entre varias aplicaciones, pero el proceso de validación no los incluirá. Los errores de validación no aparecerán para las referencias a proyectos o ensamblados que están vinculados a capas independientes cuando no aparece ninguna dependencia entre esas capas. Tales referencias no se consideran dependencias a menos que el código utilice esas referencias.

1. On the layer diagram, select one or more layers, right-click your selection, and then click **View Links**.

2. In **Layer Explorer**, look at the **Supports Validation** column. Si el valor es false, el elemento no admite la validación.

## <a name="IncludeReferences"></a> Include other .NET assemblies and projects for validation
 When you drag items to the layer diagram, references to the corresponding .NET assemblies or projects are added automatically to the **Layer References** folder in the modeling project. Esta carpeta contiene referencias a los ensamblados y proyectos que se analizan durante la validación. Puede incluir otros ensamblados y proyectos de .NET para validación sin arrastrarlos manualmente al diagrama de capas.

1. In **Solution Explorer**, right-click the modeling project or the **Layer References** folder, and then click **Add Reference**.

2. In the **Add Reference** dialog box, select the assemblies or projects, and then click **OK**.

## <a name="ValidateManually"></a> Validate code manually
 If you have an open layer diagram that is linked to solution items, you can run the **Validate** shortcut command from the diagram. You can also use the command prompt to run the **msbuild** command with the **/p:ValidateArchitecture** custom property set to **True**. Por ejemplo, cuando haga cambios en el código, realice la validación de capas con regularidad para detectar pronto los conflictos de dependencia.

#### <a name="to-validate-code-from-an-open-layer-diagram"></a>Para validar el código de un diagrama de capas abierto

1. Right-click the diagram surface, and then click **Validate Architecture**.

    > [!NOTE]
    > By default, the **Build Action** property on the layer diagram (.layerdiagram) file is set to **Validate** so that the diagram is included in the validation process.

     The **Error List** window reports any errors that occur. For more information about validation errors, see [Understand and resolve layer validation errors](#UnderstandingValidationErrors).

2. To view the source of each error, double-click the error in the **Error List** window.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] podría mostrar un mapa de código en lugar del origen del error. Esto se produce cuando el código tiene una dependencia en un ensamblado que el diagrama de capas no especifica, o al código le falta una dependencia que el diagrama de capas especifica. Revise el mapa de código o el código para determinar si debe existir la dependencia. For more information about code maps, see [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md).

3. To manage errors, see [Manage validation errors](#ManageErrors).

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

     Se mostrará cualquier error que se produzca. For more information about [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], see [MSBuild](../msbuild/msbuild.md) and [MSBuild Task](../msbuild/msbuild-task.md).

   For more information about validation errors, see [Understand and resolve layer validation errors](#UnderstandingValidationErrors).

### <a name="ManageErrors"></a> Manage validation errors
 Durante el proceso de desarrollo, puede que desee suprimir algunos de los conflictos notificados durante la validación. Por ejemplo, es posible que desee suprimir errores de los que ya se ha ocupado o que no son pertinentes para su escenario concreto. Cuando se suprime un error, conviene registrar un elemento de trabajo en [!INCLUDE[esprfound](../includes/esprfound-md.md)].

> [!WARNING]
> Ya debe estar conectado al control de código fuente TFS (SCC) para crear o vincular a un elemento de trabajo. Si intenta abrir una conexión a un SCC TFS diferente, Visual Studio cierra automáticamente la solución actual. Asegúrese de que ya está conectado al SCC apropiado antes de intentar crear o vincular a un elemento de trabajo. En las versiones posteriores de Visual Studio, los comandos de menú no están disponibles si no está conectado a un SCC.

##### <a name="to-create-a-work-item-for-a-validation-error"></a>Para crear un elemento de trabajo para un error de validación

- In the **Error List** window, right-click the error, point to **Create Work Item**, and then click the type of work item that you want to create.

  Use these tasks to manage validation errors in the **Error List** window:

|**En**|**Follow these steps**|
|------------|----------------------------|
|Suprimir los errores seleccionados durante la validación|Right-click the one or multiple selected errors, point to **Manage Validation Errors**, and then click **Suppress Errors**.<br /><br /> Los errores suprimidos aparecen tachados. La próxima vez que ejecute la validación, estos errores no aparecerán.<br /><br /> El seguimiento de los errores suprimidos se lleva a cabo en un archivo .suppressions relacionado con el archivo de diagrama de capas correspondiente.|
|Detener la supresión de los errores seleccionados|Right-click the selected suppressed error or errors, point to **Manage Validation Errors**, and then click **Stop Suppressing Errors**.<br /><br /> La próxima vez que ejecute la validación, los errores suprimidos aparecerán.|
|Restore all suppressed errors in the **Error List** window|Right-click anywhere in the **Error List** window, point to **Manage Validation Errors**, and then click **Show All Suppressed Errors**.|
|Hide all suppressed errors from the **Error List** window|Right-click anywhere in the **Error List** window, point to **Manage Validation Errors**, and then click **Hide All Suppressed Errors**.|

## <a name="ValidateAuto"></a> Validate code automatically
 Puede realizar la validación de capas cada vez que ejecute una compilación local. Si el equipo usa Team Foundation Build, podrá realizar la validación de capas con inserciones en el repositorio validadas, que se pueden especificar creando una tarea MSBuild personalizada, y usar informes de compilación para recopilar los errores de validación. To create gated check-in builds, see [Use a gated check-in build process to validate changes](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec).

#### <a name="to-validate-code-automatically-during-a-local-build"></a>Para validar código automáticamente durante una compilación local

- Use un editor de texto para abrir el archivo del proyecto de modelado (.modelproj) y, a continuación, incluya la siguiente propiedad:

```
<ValidateArchitecture>true</ValidateArchitecture>
```

 \- o -

1. In **Solution Explorer**, right-click the modeling project that contains the layer diagram or diagrams, and then click **Properties**.

2. In the **Properties** window, set the modeling project's **Validate Architecture** property to **True**.

    Esto incluye el proyecto de modelado en el proceso de validación.

3. In **Solution Explorer**, click the layer diagram (.layerdiagram) file that you want to use for validation.

4. In the **Properties** window, make sure that the diagram's **Build Action** property is set to **Validate**.

    Esto incluye el diagrama de capas en el proceso de validación.

   To manage errors in the Error List window, see [Manage Validation Errors](#ManageErrors).

#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>Para validar código automáticamente durante una compilación con Team Foundation Build

1. In **Team Explorer**, double-click the build definition, and then click **Process**.

2. Under **Build process parameters**, expand **Compilation**, and type the following in the **MSBuild Arguments** parameter:

    `/p:ValidateArchitecture=true`

   For more information about validation errors, see [Understand and resolve layer validation errors](#UnderstandingValidationErrors). Para obtener más información acerca de [!INCLUDE[esprbuild](../includes/esprbuild-md.md)], vea:

- [Compilar la aplicación](/azure/devops/pipelines/index)

- [Use the Default Template for your build process](https://msdn.microsoft.com/library/43930b12-c21b-4599-a980-2995e3d16e31)

- [Modify a Legacy Build that is Based on UpgradeTemplate.xaml](https://msdn.microsoft.com/library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)

- [Personalizar la plantilla de proceso de compilación](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

- [Monitor Progress of a Running Build](https://msdn.microsoft.com/library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)

## <a name="TroubleshootingValidation"></a> Troubleshoot layer validation issues
 En la siguiente tabla se describen problemas de validación de capas y su resolución. Estos problemas difieren de los errores que son resultado de conflictos entre el código y el diseño. For more information about these errors, see [Understand and resolve layer validation errors](#UnderstandingValidationErrors).

|**Problema**|**Possible Cause**|**Resolución**|
|---------------|------------------------|--------------------|
|Los errores de validación no se producen como se espera.|La validación no funciona en los diagramas de capas que se copian de otros diagramas de capas en el Explorador de soluciones y que están en el mismo proyecto de modelado. Los diagramas de capas que se copian de esta manera contienen las mismas referencias que el diagrama de capas original.|Agregue un nuevo diagrama de capas al proyecto de modelado.<br /><br /> Copie los elementos del diagrama de capas de origen en el nuevo diagrama.|

## <a name="UnderstandingValidationErrors"></a> Understanding and Resolving Layer Validation Errors
 Cuando se valida el código con un diagrama de capas, se producen errores de validación si el código entra en conflicto con el diseño. Por ejemplo, las siguientes condiciones podrían producir errores de validación:

- Un artefacto se ha asignado a la capa equivocada. En este caso, mueva el artefacto.

- Un artefacto, como por ejemplo una clase, usa otra clase de forma que hay conflictos con su arquitectura. En este caso, tiene que refactorizar el código para quitar la dependencia.

  Para resolver estos errores, actualice el código hasta no aparezcan más errores durante la validación. Puede realizar esta tarea repetitivamente.

  En la sección siguiente se describe la sintaxis que se usa en estos errores, se explica el significado de los mismos y se sugiere qué se puede hacer para resolverlos o administrarlos.

|**Sintaxis**|**Descripción**|
|----------------|---------------------|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* is an artifact that is associated with a layer on the layer diagram.<br /><br /> *ArtifactTypeN* is the type of *ArtifactN*, such as a **Class** or **Method**, for example:<br /><br /> MiSolución.MiProyecto.MiClase.MiMétodo(Método)|
|*NamespaceNameN*|Nombre de un espacio de nombres.|
|*LayerNameN*|Nombre de una capa del diagrama de capas.|
|*DependencyType*|The type of dependency relationship between *Artifact1* and *Artifact2*. For example, *Artifact1* has a **Calls** relationship with *Artifact2*.|

|**Error Syntax**|**Error Description**|
|----------------------|---------------------------|
|AV0001: Invalid Dependency: *Artifact1*(*ArtifactType1*) --> *Artifact2*(*ArtifactType2*)<br /><br /> Layers: *LayerName1*, *LayerName2* &#124; Dependencies: *DependencyType*|*Artifact1* in *LayerName1* should not have a dependency on *Artifact2* in *LayerName2* because *LayerName1* does not have a direct dependency on *LayerName2*.|
|AV1001: Invalid Namespace: *Artifact*<br /><br /> Layer: *LayerName* &#124; Required Namespace: *NamespaceName1* &#124; Current Namespace: *NamespaceName2*|*LayerName* requires that its associated artifacts must belong to *NamespaceName1*. *Artifact* is in *NamespaceName2*, not *NamespaceName1*.|
|AV1002: Depends on Forbidden Namespace: *Artifact1*(*ArtifactType1*) &#124; *Artifact2*(*ArtifactType2*)<br /><br /> Layer: *LayerName* &#124; Forbidden Namespace: *NamespaceName* &#124; Dependencies: *DependencyType*|*LayerName* requires that its associated artifacts must not depend on *NamespaceName*. *Artifact1* cannot depend on *Artifact2* because *Artifact2* is in *NamespaceName*.|
|AV1003: In Forbidden Namespace: *Artifact*(*ArtifactType*)<br /><br /> Layer: *LayerName* &#124; Forbidden Namespace: *NamespaceName*|*LayerName* requires that its associated artifacts cannot belong to *NamespaceName*. *Artifact* belongs to *NamespaceName*.|
|AV3001: Missing Link: Layer '*LayerName*' links to '*Artifact*' which cannot be found. ¿Falta una referencia de ensamblado?|*LayerName* links to an artifact that cannot be found. Por ejemplo, es posible que falte un vínculo a una clase porque en el proyecto de modelado falta una referencia al ensamblado que contiene la clase.|
|AV9001: El análisis de arquitectura encontró errores internos. Puede que los resultados no estén completos. Vea el registro detallado de eventos de compilación o la ventana de salida para obtener más información.|Vea el registro de eventos de compilación o la ventana de salida para obtener más información.|

## <a name="security"></a>Seguridad

## <a name="see-also"></a>Vea también
 [Validar el sistema durante el desarrollo](../modeling/validate-your-system-during-development.md)
