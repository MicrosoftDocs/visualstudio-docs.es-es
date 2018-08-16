---
title: Leer modelos y diagramas en otras ediciones de Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 4eb1b80eaa5b0af600fa45ba0cbe4786043f1580
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31948722"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Leer modelos y diagramas en otras ediciones de Visual Studio
Al abrir un modelo en una versión de Visual Studio que no es compatible con la creación de modelos, el modelo se abre en modo de solo lectura. En este modo puede cambiar el diseño de los diagramas pero no se puede cambiar el modelo.

 Para ver qué versiones de Visual Studio admiten la creación de modelos, vea [compatibilidad con la versión de arquitectura y herramientas de modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Acceder a un modelo y a diagramas
 Para leer un diagrama de dependencia, debe primero utilizar Visual Studio para abrir el proyecto de modelado y, a continuación, abra el diagrama dentro de él.

 Por esta razón, si desea leer un diagrama de dependencia, también debe tener acceso al proyecto de modelado en el que se creó. Puede hacerlo obteniendo acceso a los proyectos desde [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)] u obteniendo una copia de los archivos de proyecto.

> [!NOTE]
>  Esto no se aplica a los mapas de código ni a los diagramas de clases .NET generados a partir del código. Esos diagramas pueden verse sin necesidad de un proyecto de modelado.

 Para leer un diagrama de dependencias, el conjunto mínimo de archivos que necesita es como sigue:

-   Los dos archivos para el diagrama que desea leer, por ejemplo, de diagrama **MyDiagram.classdiagram y MyDiagram.classdiagram.layout**.

    > [!NOTE]
    >  Para los diagramas de dependencia, también debe tener el archivo que se denomina * MyDiagram ***. layerdiagram.suppressions**.

-   El modelado del archivo de proyecto (**MyModel.modelproj**)

-   El archivo de modelo raíz (**ModelDefinition\MyModel. UML**)

-   Los archivos del paquete para los paquetes que se hace referencia en el diagrama (**ModelDefinition\MyPackage.uml**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Cambios que puede realizar en modo de solo lectura
 Si abre un modelo y sus diagramas en una versión de Visual Studio que no es compatible con la creación de modelos, no podrá cambiar el modelo. Es decir, no podrá cambiar los elementos y relaciones que se muestran en los diagramas o en el explorador de modelos. Sin embargo, puede realizar algunos cambios en el diseño de los diagramas:

-   Reorganizar las formas y conectores del diagrama.

-   Expandir y contraer formas.

 Puede guardar estos cambios. Si desea que los cambios visibles para otros usuarios, por lo menos debe enviar la actualización **. Layout** archivos.

##  <a name="RelatedTopics"></a> Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)|Un diagrama de capas muestra la estructura de una arquitectura existente o propuesta. Cuando se escribe código, se puede validar automáticamente con un diagrama de capas.|

## <a name="see-also"></a>Vea también

- [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)