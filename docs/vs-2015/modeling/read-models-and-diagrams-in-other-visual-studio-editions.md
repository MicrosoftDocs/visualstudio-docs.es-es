---
title: Leer modelos y diagramas en otras ediciones de Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
ms.assetid: 46eee279-a9e4-4742-a024-5bd2cf032b86
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a6a7c944eb3d5378ad0fc1542b90ad182f7eb976
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671289"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Leer modelos y diagramas en otras ediciones de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al abrir un modelo en una versión de Visual Studio que no es compatible con la creación de modelos, el modelo se abre en modo de solo lectura. En este modo puede cambiar el diseño de los diagramas pero no se puede cambiar el modelo.

 Para ver qué versiones de Visual Studio admiten la creación de modelos, vea [compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Acceder a un modelo y a diagramas
 Para leer un diagrama UML o un diagrama de capas, primero debe usar Visual Studio para abrir el proyecto de modelado y, después, abrir el diagrama dentro de él.

 Por este motivo, si desea leer un diagrama UML o un diagrama de capas, también debe tener acceso al proyecto de modelado en el que se creó. Puede hacerlo obteniendo acceso a los proyectos desde [!INCLUDE[esprscc](../includes/esprscc-md.md)] u obteniendo una copia de los archivos de proyecto.

> [!NOTE]
> Esto no se aplica a los mapas de código ni a los diagramas de clases .NET generados a partir del código. Esos diagramas pueden verse sin necesidad de un proyecto de modelado.

 Para leer un diagrama UML o un diagrama de capas, necesita el siguiente conjunto mínimo de archivos:

- Los dos archivos de diagrama del diagrama que desea leer, por ejemplo, **diagram. classdiagram y diagram. classdiagram. layout**.

    > [!NOTE]
    > En el caso de los diagramas de capas, también debe tener el archivo denominado _Diagram_**. layerdiagram. suppresss**.

- Archivo del proyecto de modelado (**modelproj**)

- El archivo de modelo raíz (**ModelDefinition\MyModel.UML**)

- Los archivos de paquete de cualquier paquete al que se hace referencia en el diagrama (**ModelDefinition\MyPackage.UML**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Cambios que puede realizar en modo de solo lectura
 Si abre un modelo y sus diagramas en una versión de Visual Studio que no es compatible con la creación de modelos, no podrá cambiar el modelo. Es decir, no podrá cambiar los elementos y relaciones que se muestran en los diagramas o en el explorador de modelos. Sin embargo, puede realizar algunos cambios en el diseño de los diagramas:

- Reorganizar las formas y conectores del diagrama.

- Expandir y contraer formas.

  Puede guardar estos cambios. Si desea que los cambios sean visibles para otros usuarios, debe enviar al menos los archivos **. layout** actualizados.

## <a name="related-topics"></a><a name="RelatedTopics"></a> Temas relacionados

|Título|Descripción|
|-----------|-----------------|
|[Diagramas de capas: referencia](../modeling/layer-diagrams-reference.md)|Un diagrama de capas muestra la estructura de una arquitectura existente o propuesta. Cuando se escribe código, se puede validar automáticamente con un diagrama de capas.|
|[Diagramas de actividades UML: referencia](../modeling/uml-activity-diagrams-reference.md)|Un diagrama de actividad muestra un flujo de trabajo, ya sea en un proceso empresarial o en software.|
|[Diagramas de clases de UML: Referencia](../modeling/uml-class-diagrams-reference.md)|Un diagrama de clase muestra tipos y relaciones que se usan en muchos contextos, como el código, los esquemas de base de datos, los protocolos de comunicaciones o el glosario de términos usados para describir un dominio empresarial.|
|[Diagramas de componentes de UML: Referencia](../modeling/uml-component-diagrams-reference.md)|Un diagrama de componentes muestra partes que se pueden separar en un diseño de software y sus interfaces.|
|[Diagramas de secuencia UML: referencia](../modeling/uml-sequence-diagrams-reference.md)|Un diagrama de secuencia muestra las interacciones entre los elementos de un diseño de software.|
|[Diagramas de casos de uso de UML: referencia](../modeling/uml-use-case-diagrams-reference.md)|Un diagrama de casos de uso muestra los usuarios de un sistema y las actividades que pueden realizar para lograr objetivos concretos.|

## <a name="see-also"></a>Consulte también
 [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)
