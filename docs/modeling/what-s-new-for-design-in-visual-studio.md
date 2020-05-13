---
title: Novedades de diseño en Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 6f81cc32604abe6d90ac0d263574e97df35c63bd
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301498"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Novedades de diseño en Visual Studio 2017

## <a name="live-dependency-validation"></a>Validación de dependencias en vivo

La eliminación de dependencias no deseadas es una parte importante de la gestión de su deuda técnica. Visual Studio proporciona validación en vivo de dependencias, incluida información precisa sobre los problemas, como dónde se encuentran. La validación de dependencias en vivo aprovecha todas las ventajas de las nuevas características de la lista de errores y el editor.

![Validación de dependencias en vivo en acción](media/dep-validation-whatsnew-01.png)

La experiencia de creación ha cambiado para que la validación de dependencias sea más reconocible y más accesible. La terminología ha cambiado de "diagrama de capa" a "diagrama de dependencia".

El menú **Arquitectura** ahora contiene un comando para crear directamente un diagrama de dependencia:

![Elemento de dependencia en vivo en el menú Arquitectura](media/dep-validation-whatsnew-02.png)

Los nombres y descripciones de las propiedades de capa se han cambiado para que sean más significativos:

![Nombres de propiedades actualizados de dependencias en vivo](media/dep-validation-whatsnew-03.png)

Inmediatamente verá el impacto de los cambios en los resultados del análisis para el código actual en la solución cada vez que guarde el diagrama. No tiene que esperar a la finalización del comando **Validar dependencias.**

Consulte [esta entrada de blog](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/) para obtener más información.

## <a name="uml-designers-have-been-removed"></a>Se han eliminado los diseñadores de UML

Los diseñadores de UML se han quitado de Visual Studio.

* Los diagramas UML ahora se presentan como archivos XML
* El Explorador de modelos UML ya no existe
* Las referencias de proyecto de modelado ya no se utilizan para la validación de dependencias
* El nodo "Referencias de capa" en el Explorador de soluciones ya no se muestra
* La acción de compilación "Validar" en un diagrama de dependencia (capa) ya no se utiliza: la tarea De compilar se ha eliminado
* La estructura del proyecto se mantiene para el ida y vuelta entre versiones
* Todavía puede abrir, crear, editar y guardar un diagrama de dependencia (capa) como XML
* Los elementos de trabajo de TFS vinculados a un diagrama de dependencia (capa) no son accesibles en la superficie de diseño
* La vinculación posterior de DSL o una capa ya no es compatible
* Ya no se admite la extensibilidad UML en el SDK de modelado

La compatibilidad para visualizar la arquitectura de código .NET y C++ está disponible a través de mapas de [código.](map-dependencies-across-your-solutions.md)

Si es un usuario importante de los diseñadores de UML, puede seguir usando Visual Studio 2015 o versiones anteriores mientras decide una herramienta alternativa para sus necesidades de UML.

Consulte [esta entrada de blog](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/) para obtener más información.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Soporte de edición para herramientas de arquitectura y modelado

Visual Studio está disponible en varias ediciones. No todos estos proporcionan soporte para las herramientas de arquitectura y modelado. En la tabla siguiente se muestra la disponibilidad de cada herramienta.

|**Característica**|**Edición Enterprise**|**Edición profesional**|**Edición comunitaria**|
|-|-|-|-|
|**Mapas de código**|Sí|Solo admite la lectura de mapas de código, el filtrado de mapas de código, la adición de nuevos nodos genéricos y la creación de un nuevo gráfico dirigido a partir de una selección.|-|
|**Diagramas de dependencia**|Sí|Solo admite la lectura de diagramas de dependencia.|Solo admite la lectura de diagramas de dependencia.|
|**Gráficos dirigidos** (diagramas DGML)|Sí|Sí|Sí|
|**Clon de código**|Sí|-|-|
