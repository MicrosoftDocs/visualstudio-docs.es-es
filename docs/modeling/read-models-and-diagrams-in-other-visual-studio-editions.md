---
title: Leer modelos y diagramas en otras ediciones de Visual Studio
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d8366c0f87830a77f550dabbce2e8f875171418
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823986"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Leer modelos y diagramas en otras ediciones de Visual Studio

Al abrir un modelo en una versión de Visual Studio que no es compatible con la creación de modelos, el modelo se abre en modo de solo lectura. En este modo puede cambiar el diseño de los diagramas pero no se puede cambiar el modelo.

Para ver qué versiones de Visual Studio admite la creación de modelos, vea [compatibilidad con la versión de arquitectura y las herramientas de modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Acceder a un modelo y a diagramas

Para leer un diagrama de dependencia, debe usar Visual Studio para abrir el proyecto de modelado y, a continuación, abra el diagrama dentro de él.

Por este motivo, si desea leer un diagrama de dependencia, también debe tener acceso al proyecto de modelado en el que se creó. Para ello, acceso a los proyectos de control de código fuente, o mediante la obtención de una copia de los archivos del proyecto.

> [!NOTE]
> Esto no se aplica a los mapas de código ni a los diagramas de clases .NET generados a partir del código. Esos diagramas pueden verse sin necesidad de un proyecto de modelado.

Para leer un diagrama de dependencia, el conjunto mínimo de archivos que necesita es como sigue:

- Los dos archivos de diagrama que desea leer, por ejemplo, de diagrama **MyDiagram.classdiagram y MyDiagram.classdiagram.layout**.

    > [!NOTE]
    > Para diagramas de dependencia, también debe tener el archivo que se denomina _MyDiagram_**. layerdiagram.suppressions**.

- El modelado del archivo de proyecto (**MyModel.modelproj**)

- El archivo de modelo raíz (**ModelDefinition\MyModel. UML**)

- Los archivos del paquete para los paquetes que se hace referencia en el diagrama (**ModelDefinition\MyPackage.uml**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Cambios que puede realizar en modo de solo lectura

Si abre un modelo y sus diagramas en una versión de Visual Studio que no es compatible con la creación de modelos, no podrá cambiar el modelo. Es decir, no podrá cambiar los elementos y relaciones que se muestran en los diagramas o en el explorador de modelos. Sin embargo, puede realizar algunos cambios en el diseño de los diagramas:

- Reorganizar las formas y conectores del diagrama.

- Expandir y contraer formas.

Puede guardar estos cambios. Si desea que los cambios sea visible para otros usuarios, debe enviar al menos la actualización **.layout** archivos.

## <a name="see-also"></a>Vea también

- [Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)
- [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)