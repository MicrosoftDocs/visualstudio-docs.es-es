---
title: Create models for your app | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.common.commentlink.properties
- vs.teamarch.UMLModelExplorer.dependency
- vs.teamarch.UMLModelExplorer.commentlink
- vs.teamarch.common.dependency.properties
- Microsoft.VisualStudio.Uml.Diagrams.CommentShape.IsTransparent
- vs.teamarch.common.comment.properties
- vs.teamarch.UMLModelExplorer.comment
helpviewer_keywords:
- diagrams - modeling, sequence
- software design
- diagrams - modeling, use case
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML model
- diagrams - modeling, UML use case
- diagrams - modeling, class
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- software modeling
- diagrams - modeling, UML sequence
- UML
- diagrams - modeling, UML
- diagrams - modeling, layer
- software, designing
- diagrams - modeling, UML class
- software, modeling
- UML diagrams
ms.assetid: b69d9d91-c7e7-4dee-8eb6-706076eecb85
caps.latest.revision: 60
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a9f20629c39bc37ca20550c3b88d8ecb2aca470f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300247"
---
# <a name="create-models-for-your-app"></a>Crear modelos para la aplicación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los diagramas de modelado le ayudan a entender, aclarar y transmitir las ideas que tiene sobre su código y los requisitos del usuario que el sistema de software debe satisfacer. Por ejemplo, para describir y transmitir los requisitos de los usuarios, puede usar diagramas de casos de uso, de actividades, de clases y de secuencia del Lenguaje unificado de modelado (UML). Para describir y transmitir la funcionalidad del sistema, puede usar los diagramas de componentes, clases, actividades y secuencia de UML.

 See [Channel 9 Video: Improve architecture through modeling](https://go.microsoft.com/fwlink/?LinkID=252078).

 Puede crear los siguientes diagramas de UML en esta versión:

|**Diagram**|**Qué muestra**|
|-----------------|---------------|
|[Diagramas de actividades UML: referencia](../modeling/uml-activity-diagrams-reference.md)|El flujo de trabajo entre las acciones y los participantes de un proceso de negocio|
|[Diagramas de componentes de UML: referencia](../modeling/uml-component-diagrams-reference.md)|Los componentes de un sistema, sus interfaces, puertos y relaciones|
|[Diagramas de clases de UML: referencia](../modeling/uml-class-diagrams-reference.md)|Los tipos que se usan para almacenar e intercambiar datos en el sistema y sus relaciones|
|[Diagramas de secuencia UML: referencia](../modeling/uml-sequence-diagrams-reference.md)|Las secuencias de interacciones entre los objetos, componentes, sistemas o actores|
|[Diagramas de casos de uso de UML: referencia](../modeling/uml-use-case-diagrams-reference.md)|Los objetivos y tareas de los usuarios que admite un sistema|

 To see which versions of Visual Studio support each type of diagram, see [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Para visualizar la arquitectura de un sistema o código existente, cree los diagramas siguientes:

|**Diagram**|**Qué muestra**|
|-----------------|---------------|
|[Diagrama de capas: instrucciones](../modeling/layer-diagrams-guidelines.md)<br /><br /> [Diagramas de capas: referencia](../modeling/layer-diagrams-reference.md)|La arquitectura de alto nivel del sistema|
|Mapas de código<br /><br /> [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)<br /><br /> [Buscar posibles problemas mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)|Las dependencias y otras relaciones en el código|
|Diagramas de clases generadas por código<br /><br /> [Trabajar con diagramas de clases (Diseñador de clases)](../ide/working-with-class-diagrams-class-designer.md)|Los tipos y sus relaciones en el código .NET|

## <a name="common-tasks"></a>Tareas comunes

|**Topic**|**Task**|
|---------------|--------------|
|[Crear proyectos y diagramas de modelado UML](../modeling/create-uml-modeling-projects-and-diagrams.md)|**Create models** and add diagrams.|
|[Editar modelos y diagramas UML](../modeling/edit-uml-models-and-diagrams.md)|**Draw diagrams** to edit the model.|
|[Definir paquetes y espacios de nombres](../modeling/define-packages-and-namespaces.md)|**Create packages** to divide a model into units that different team members can work on.|
|[Generar código a partir de diagramas de clases UML](../modeling/generate-code-from-uml-class-diagrams.md)|**Generate C# code from class diagrams** to start your implementation.|
|[Personalizar el modelo con perfiles y estereotipos](../modeling/customize-your-model-with-profiles-and-stereotypes.md)|**Customize model elements** using stereotypes, to extend the standard UML model elements for specific purposes.|
|[Vincular elementos de modelo con elementos de trabajo](../modeling/link-model-elements-and-work-items.md)|**Create links between model elements and work items** to help you track tasks, test cases, bugs, requirements, issues, or other kinds of work that are associated with specific parts of your model.|
|[Exportar diagramas como imágenes](../modeling/export-diagrams-as-images.md)|**Save your model and diagrams** so that you can share them with other users, including those who do not use [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].|

## <a name="related-tasks"></a>Tareas relacionadas

|**Topic**|**Task**|
|---------------|--------------|
|[Visualizar el código](../modeling/visualize-code.md)|Crear mapas de código y diagramas de capas para entender el código con el que no se está familiarizado.|
|[Requisitos del usuario de modelos](../modeling/model-user-requirements.md)|Usar modelos para aclarar y transmitir las necesidades del usuario.|
|[Modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md)|Usar modelos para describir la estructura y el comportamiento global del sistema y para asegurarse de que satisface las necesidades de los usuarios.|
|[Validar el sistema durante el desarrollo](../modeling/validate-your-system-during-development.md)|Asegurarse de que el software es coherente con las necesidades de los usuarios y la arquitectura global del sistema.|
|[Usar modelos en el proceso de desarrollo](../modeling/use-models-in-your-development-process.md)<br /><br /> [Use models in Agile development](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)|Usar modelos para que resulte más fácil entender y cambiar el sistema durante su desarrollo.|
|[Estructurar la solución de modelado](../modeling/structure-your-modeling-solution.md)|Organizar los modelos en un proyecto de tamaño grande o mediano.|

## <a name="external-resources"></a>Recursos externos

|**Categoría**|**Links**|
|------------------|---------------|
|**Foros**|-   [Herramientas de visualización y modelado de Visual Studio](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [SDK de visualización y modelado de Visual Studio (Herramientas ADSL)](https://go.microsoft.com/fwlink/?LinkId=184721)|
