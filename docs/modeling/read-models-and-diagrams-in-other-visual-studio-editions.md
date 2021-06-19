---
title: Leer modelos y diagramas en otras ediciones de Visual Studio
description: Obtenga información sobre la lectura de modelos y diagramas en Visual Studio, así como el comportamiento de solo lectura cuando se usa una versión de Visual Studio que no admite la creación de modelos.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 95fbf6451a3f07581ff2bdb098428f41904d4276
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389909"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Leer modelos y diagramas en otras ediciones de Visual Studio

Al abrir un modelo en una versión de Visual Studio que no es compatible con la creación de modelos, el modelo se abre en modo de solo lectura. En este modo puede cambiar el diseño de los diagramas pero no se puede cambiar el modelo.

Para ver qué versiones de Visual Studio admiten la creación de modelos, vea [Compatibilidad con versiones para herramientas](../modeling/analyze-and-model-your-architecture.md#VersionSupport)de arquitectura y modelado .

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Acceder a un modelo y a diagramas

Para leer un diagrama de dependencias, primero debe usar Visual Studio para abrir el proyecto de modelado y, a continuación, abrir el diagrama dentro de él.

Por este motivo, si desea leer un diagrama de dependencias, también debe tener acceso al proyecto de modelado en el que se creó. Para ello, puede acceder al proyecto desde el control de código fuente o obtener una copia de los archivos del proyecto.

> [!NOTE]
> Esto no se aplica a los mapas de código ni a los diagramas de clases .NET generados a partir del código. Esos diagramas pueden verse sin necesidad de un proyecto de modelado.

Para leer un diagrama de dependencias, el conjunto mínimo de archivos que necesita es el siguiente:

- Los dos archivos de diagrama para el diagrama que desea leer, por ejemplo, **MyDiagram.classdiagram y MyDiagram.classdiagram.layout**.

    > [!NOTE]
    > Para los diagramas de dependencias, también debe tener el archivo denominado _MyDiagram_**.layerdiagram.suppressions.**

- El archivo de proyecto de modelado (**MyModel.modelproj**)

- El archivo de modelo raíz (**ModelDefinition\MyModel.uml**)

- Los archivos de paquete para cualquier paquete al que se hace referencia en el diagrama (**ModelDefinition\MyPackage.uml**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Cambios que puede realizar en modo de solo lectura

Si abre un modelo y sus diagramas en una versión de Visual Studio que no es compatible con la creación de modelos, no podrá cambiar el modelo. Es decir, no podrá cambiar los elementos y relaciones que se muestran en los diagramas o en el explorador de modelos. Sin embargo, puede realizar algunos cambios en el diseño de los diagramas:

- Reorganizar las formas y conectores del diagrama.

- Expandir y contraer formas.

Puede guardar estos cambios. Si desea que los cambios sean visibles para otros usuarios, debe enviar al menos los archivos **.layout** actualizados.

## <a name="see-also"></a>Vea también

- [Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)
- [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)
