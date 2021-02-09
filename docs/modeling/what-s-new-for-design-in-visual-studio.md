---
title: Novedades de diseño en Visual Studio 2017
description: Obtenga información sobre las nuevas características del diseño de código, como la validación de dependencias dinámicas, que están disponibles en Visual Studio 2017.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 00a72f52b67e1e55bcc0699a3daf7da4dcfbc57d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924010"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Novedades de diseño en Visual Studio 2017

## <a name="live-dependency-validation"></a>Validación de dependencias en vivo

Quitar las dependencias no deseadas es una parte importante de la administración de la deuda técnica. Visual Studio proporciona la validación en vivo de las dependencias, incluida la información precisa sobre problemas, como dónde se encuentran. La validación de dependencias en vivo aprovecha las nuevas características del Lista de errores y el editor.

![Validación de dependencias dinámicas en acción](media/dep-validation-whatsnew-01.png)

La experiencia de creación ha cambiado para que la validación de dependencias sea más reconocible y más accesible. La terminología ha cambiado de "diagrama de capas" a "diagrama de dependencias".

El menú **arquitectura** contiene ahora un comando para crear directamente un diagrama de dependencia:

![Elemento de dependencia activo en el menú arquitectura](media/dep-validation-whatsnew-02.png)

Los nombres y descripciones de las propiedades de capa se han modificado para que sean más significativos:

![Nombres de propiedad actualizados de dependencias dinámicas](media/dep-validation-whatsnew-03.png)

Verá inmediatamente el impacto de los cambios en los resultados del análisis para el código actual de la solución cada vez que guarde el diagrama. No es necesario esperar a que se complete el comando de **validación de dependencias** .

Consulte [esta entrada de blog](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/) para obtener más información.

## <a name="uml-designers-have-been-removed"></a>Se han quitado los diseñadores de UML

Los diseñadores de UML se han quitado de Visual Studio.

* Los diagramas de UML ahora se presentan como archivos XML
* El explorador de modelos UML ya no existe
* Las referencias del proyecto de modelado ya no se utilizan para la validación de dependencias
* Ya no se muestra el nodo "referencias de capa" en Explorador de soluciones
* Ya no se usa la acción de compilación "validar" en un diagrama de dependencia (capa). la tarea de compilación se ha quitado.
* La estructura del proyecto se mantiene para recorridos de ida y vuelta entre versiones
* Todavía puede abrir, crear, editar y guardar un diagrama de dependencia (capa) como XML
* No se puede obtener acceso a los elementos de trabajo de TFS vinculados a un diagrama de dependencia (capa) en la superficie de diseño
* Ya no se admite la vinculación inversa desde a DSL o a una capa
* Ya no se admite la extensibilidad de UML en el SDK de modelado

La compatibilidad con la visualización de la arquitectura del código de .NET y C++ está disponible a través de [mapas de código](map-dependencies-across-your-solutions.md).

Si es un usuario importante de los diseñadores de UML, puede seguir usando Visual Studio 2015 o versiones anteriores mientras decide una herramienta alternativa para sus necesidades de UML.

Consulte [esta entrada de blog](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/) para obtener más información.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Compatibilidad de edición con las herramientas de arquitectura y modelado

Visual Studio está disponible en varias ediciones. No todas estas proporcionan compatibilidad con las herramientas de arquitectura y modelado. En la tabla siguiente se muestra la disponibilidad de cada herramienta.

|**Característica**|**Edición Enterprise**|**Professional Edition**|**Community Edition**|
|-|-|-|-|
|**Mapas de código**|Sí|Solo admite la lectura de mapas de código, el filtrado de mapas de código, la adición de nuevos nodos genéricos y la creación de un nuevo gráfico dirigido a partir de una selección.|-|
|**Diagramas de dependencias**|Sí|Solo admite la lectura de diagramas de dependencia.|Solo admite la lectura de diagramas de dependencia.|
|**Gráficos dirigidos** (diagramas de DGML)|Sí|Sí|Sí|
|**Clon de código**|Sí|-|-|
