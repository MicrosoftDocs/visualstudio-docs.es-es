---
title: Novedades de diseño en Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- what's new [VIsual Studio ALM], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio ALM], What's New
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c25d89ae3ab3d25e415b4407a46fc903b1c05266
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33870967"
---
# <a name="whats-new-for-design-in-visual-studio"></a>Novedades de diseño en Visual Studio

## <a name="live-dependency-validation"></a>Validación de la dependencia en vivo

Quitar dependencias no deseadas es una parte importante de la administración de la deuda técnica. Validación en vivo de las dependencias es ahora incluye, proporcionar información precisa acerca de los problemas y totalmente beneficien de las nuevas características de la lista de errores y el editor.

![Validación de dependencia en vivo en acción](media/dep-validation-whatsnew-01.png)

Ha cambiado la experiencia de creación para realizar validación de dependencia más reconocible y sea más accesible, cambiar la terminología de "Diagrama de capas" a "Diagrama de dependencia".

El **arquitectura** menú ahora contiene un comando para crear directamente un diagrama de dependencia:

![Elemento de dependencia en vivo en el menú de arquitectura](media/dep-validation-whatsnew-02.png)

... y los nombres de propiedad de una capa en un diagrama de dependencias y sus descripciones, han cambiado para que tuvieran más sentido:

![Nombres de propiedad de dependencia en vivo actualizado](media/dep-validation-whatsnew-03.png)

Ahora verá el impacto de los cambios inmediatamente en los resultados del análisis para el código actual en la solución cada vez que guarde el diagrama. No tiene que esperar la finalización del comando "Validar dependencias" ya.

Para obtener más información, consulte [esta entrada de blog](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/07/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Se han quitado los diseñadores de UML

Los diseñadores UML se han quitado de esta versión de Visual Studio Enterprise.

* UML (diagramas) ahora se presentan como archivos XML
* El Explorador de modelos UML ya no existe
* Las referencias ya no se utilizan para la validación de la dependencia de proyecto de modelado
* Ya no se muestra el nodo de "Referencias de capa" en el Explorador de soluciones
* Ya no se usa la acción de compilación "Validación" en un diagrama de dependencia (nivel): se ha quitado la tarea de compilación
* Se mantiene la estructura del proyecto de ida y vuelta entre versiones
* Todavía puede abrir, crear, editar y guardar un diagrama de dependencia (capa) como XML
* Elementos de trabajo TFS vinculados a un diagrama de dependencia (capa) no son accesibles en la superficie de diseño
* Ya no se admite la vinculación atrás de DSL o una capa
* Ya no se admite la extensibilidad UML en el SDK de modelado

Sin embargo, es compatibles con la visualización de la arquitectura del código de .NET y C++ a través de [mapas de código](map-dependencies-across-your-solutions.md)y las mejoras importantes de la validación de dependencia se ha descrito anteriormente.

Si es un usuario significativo de los diseñadores UML, puede continuar utilizando Visual Studio 2015 o versiones anteriores, mientras que decida una herramienta alternativa para sus necesidades UML.

Para obtener más información, consulte [esta entrada de blog](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/14/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="a-nameversionsupport-version-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Compatibilidad con la versión de arquitectura y herramientas de modelado

Visual Studio 2015 está disponible en varias versiones. No todos ellos proporcionan compatibilidad para la arquitectura y las herramientas de modelado. En la tabla siguiente se muestra la disponibilidad de cada herramienta.

|**Característica**|**Enterprise**|**Professional**|**Community**|**Express**|
|-----------------|--------------------|----------------------|-------------------|-----------------|
|**Mapas de código**|Sí|Solo se admite la lectura de mapas de código, filtrando código asigna, agregar nuevos nodos genéricos y crear un nuevo gráfico dirigido a partir de una selección.|-|-|
|**Diagramas de dependencia**|Sí|Solo admite la lectura de diagramas de dependencia.|Solo admite la lectura de diagramas de dependencia.|-|
|**Gráficos dirigidos** (diagramas DGML)|Sí|Sí|Sí|-|
|**Clon de código**|Sí|-|-|-|