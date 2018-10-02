---
title: Referencia de esquemas del archivo del proyecto MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 134a66a38886201a9f53ed5d15dda009b095d72f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567139"
---
# <a name="msbuild-project-file-schema-reference"></a>Referencia de esquemas del archivo de proyecto MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [referencia de esquema de archivo de proyecto de MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-project-file-schema-reference).  
  
  
Proporciona una tabla de todos los elementos de esquema XML [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] con los atributos disponibles y elementos secundarios.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] utiliza archivos del proyecto para indicar al motor de compilación qué y cómo debe compilar. Los archivos del proyecto [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] son archivos XML que cumplen el esquema XML [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. En esta sección se documenta el archivo de definición (.xsd) del esquema XML para [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
## <a name="msbuild-xml-schema-elements"></a>Elementos de esquema XML de MSBuild  
 En la tabla siguiente se enumeran todos los elementos de esquema XML [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] junto con sus elementos secundarios y atributos.  
  
|Elemento|Elementos secundarios|Atributos|  
|-------------|--------------------|----------------|  
|[Elemento Choose (MSBuild)](../msbuild/choose-element-msbuild.md)|Otherwise<br /><br /> Cuando|--|  
|[Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)|--|Condición<br /><br /> Proyecto|  
|[Elemento ImportGroup](../msbuild/importgroup-element.md)|Importar|Condición|  
|[Elemento Item (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|Condición<br /><br /> Excluir<br /><br /> Incluir<br /><br /> Quitar|  
|[Elemento ItemDefinitionGroup (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Item*|Condición|  
|[Elemento ItemGroup (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Item*|Condición|  
|[Elemento ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Item*|Condición|  
|[Elemento OnError (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Condición<br /><br /> ExecuteTargets|  
|[Elemento Otherwise (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Elegir<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|  
|[Elemento Output (MSBuild)](../msbuild/output-element-msbuild.md)|--|Condición<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> TaskParameter|  
|[Elemento Parameter](../msbuild/parameter-element.md)|--|Salida<br /><br /> ParameterType<br /><br /> Obligatorio|  
|[Elemento ParameterGroup](../msbuild/parametergroup-element.md)|*Parameter*|--|  
|[Elemento Project (MSBuild)](../msbuild/project-element-msbuild.md)|Elegir<br /><br /> Importar<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> Destino<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|  
|[Elemento ProjectExtensions (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|  
|[Elemento Property (MSBuild)](../msbuild/property-element-msbuild.md)|--|Condición|  
|[Elemento PropertyGroup (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Property*|Condición|  
|[Elemento Target (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Task*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Condición<br /><br /> DependsOnTargets<br /><br /> Entradas<br /><br /> KeepDuplicateOutputs<br /><br /> nombre<br /><br /> Salidas<br /><br /> Valores devueltos|  
|[Elemento Task (MSBuild)](../msbuild/task-element-msbuild.md)|Salida|Condición<br /><br /> ContinueOnError<br /><br /> *Parameter*|  
|[Elemento TaskBody (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Data*|Evaluate|  
|[Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> TaskBody|AssemblyFile<br /><br /> AssemblyName<br /><br /> Condición<br /><br /> TaskFactory<br /><br /> TaskName|  
|[Elemento When (MSBuild)](../msbuild/when-element-msbuild.md)|Elegir<br /><br /> ItemGroup<br /><br /> PropertyGroup|Condición|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Condiciones](../msbuild/msbuild-conditions.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](msbuild.md)


