---
title: Referencia de esquemas del archivo del proyecto MSBuild | Microsoft Docs
description: Consulte una tabla en la que se enumeran todos los elementos de esquema XML de MSBuild con los atributos y elementos secundarios disponibles.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 549e78309ef5fc5e9baf4237f9eca8c7484bc198
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046160"
---
# <a name="msbuild-project-file-schema-reference"></a>Referencia de esquemas del archivo del proyecto MSBuild

Proporciona una tabla de todos los elementos de esquema XML de MSBuild con los atributos y elementos secundarios disponibles.

 MSBuild utiliza archivos del proyecto para indicar al motor de compilación qué debe compilar y cómo. Los archivos del proyecto de MSBuild son archivos XML que cumplen el esquema XML de MSBuild. En esta sección se documenta el archivo de definición de esquema XML ( *.xsd* ) para MSBuild.

El vínculo de esquema de un archivo de proyecto de MSBuild no es necesario en Visual Studio 2017 y versiones posteriores. Si está presente, debe ser ` http://schemas.microsoft.com/developer/msbuild/2003` independientemente de la versión de Visual Studio.

## <a name="msbuild-xml-schema-elements"></a>Elementos de esquema XML de MSBuild

 En la tabla siguiente se enumeran todos los elementos de esquema XML de MSBuild junto con sus elementos secundarios y atributos.

|Elemento|Elementos secundarios|Atributos|
|-------------|--------------------|----------------|
|[Elemento Choose (MSBuild)](../msbuild/choose-element-msbuild.md)|Otherwise<br /><br /> Cuando|--|
|[Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)|--|Condición<br /><br /> Project|
|[Elemento ImportGroup](../msbuild/importgroup-element.md)|Importar|Condición|
|[Elemento Item (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|Condición<br /><br /> Exclude<br /><br /> Incluir<br /><br /> Quitar|
|[Elemento ItemDefinitionGroup (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Elemento*|Condición|
|[Elemento ItemGroup (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Elemento*|Condición|
|[Elemento ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Elemento*|Condición|
|[Elemento OnError (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Condición<br /><br /> ExecuteTargets|
|[Elemento Otherwise (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Elegir<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|
|[Elemento Output (MSBuild)](../msbuild/output-element-msbuild.md)|--|Condición<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> TaskParameter|
|[Elemento Parameter](../msbuild/parameter-element.md)|--|Resultados<br /><br /> ParameterType<br /><br /> Requerido|
|[ParameterGroup (Elemento)](../msbuild/parametergroup-element.md)|*Parámetro*|--|
|[Elemento Project (MSBuild)](../msbuild/project-element-msbuild.md)|Elegir<br /><br /> Importar<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> Destino<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|
|[Elemento ProjectExtensions (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Elemento Property (MSBuild)](../msbuild/property-element-msbuild.md)|--|Condición|
|[Elemento PropertyGroup (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Propiedad*|Condición|
|[Elemento Sdk (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|Nombre<br /><br /> Versión|
|[Elemento Target (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Task*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Condición<br /><br /> DependsOnTargets<br /><br /> Entradas<br /><br /> KeepDuplicateOutputs<br /><br /> Name<br /><br /> Salidas<br /><br /> Devoluciones|
|[Elemento Task de Target (MSBuild)](../msbuild/task-element-msbuild.md)|Resultados|Condición<br /><br /> ContinueOnError<br /><br /> *Parámetro*|
|[Elemento Task de UsingTask (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Data*|Evaluate|
|[Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> Tarea|AssemblyFile<br /><br /> AssemblyName<br /><br /> Condición<br /><br /> TaskFactory<br /><br /> TaskName|
|[Elemento When (MSBuild)](../msbuild/when-element-msbuild.md)|Elegir<br /><br /> ItemGroup<br /><br /> PropertyGroup|Condición|

## <a name="see-also"></a>Vea también

- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
- [Condiciones](../msbuild/msbuild-conditions.md)
- [Referencia de MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
