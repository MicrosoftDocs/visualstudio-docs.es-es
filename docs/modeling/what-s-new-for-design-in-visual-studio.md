---
title: "¿Qué &#39; s nuevo para el diseño en Visual Studio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- what's new [VIsual Studio ALM], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio ALM], What's New
ms.assetid: 36ab5c17-6dc0-4075-a28e-a0fa49b11260
caps.latest.revision: "32"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.workload: multiple
ms.openlocfilehash: 137ca47d83e0540a7d0b3959d7d806dbf3d5f3a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="what39s-new-for-design-in-visual-studio"></a>¿Qué &#39; s nuevo para el diseño en Visual Studio

## <a name="live-dependency-validation"></a>Validación de la dependencia en vivo

Quitar dependencias no deseadas es una parte importante de la administración de la deuda técnica.
Validación en vivo de las dependencias es ahora incluye, proporcionar información precisa acerca de los problemas y totalmente beneficien de las nuevas características de la lista de errores y el editor.

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

<a name="VersionSupport"></a>
##  <a name="version-support-for-architecture-and-modeling-tools"></a>Compatibilidad de versiones con las herramientas de arquitectura y modelado  

Visual Studio está disponible en varias versiones. No todas son compatibles con las herramientas de arquitectura y modelado. En la tabla siguiente se muestra la disponibilidad de cada herramienta.  
  
|**Característica**|**Enterprise**|**Professional**|**Community**|**Express**|  
|-----------------|--------------------|----------------------|-------------------|-----------------|  
|**Mapas de código**|Sí|Vea la nota (1)|-|-|  
|**Diagramas de dependencia**|Sí|Vea la nota (2)|Vea la nota (2)|-|  
|**Gráficos dirigidos** (diagramas DGML)|Sí|Sí|Sí|-|  
|**Clon de código**|Sí|-|-|-|  
  
Nota (1): Solo admite la lectura de mapas de código, el filtrado de mapas de código, la adición de nuevos nodos genéricos y la creación de un nuevo gráfico dirigido a partir de una selección.

Nota (2): Solo admite la lectura diagramas de dependencia.
