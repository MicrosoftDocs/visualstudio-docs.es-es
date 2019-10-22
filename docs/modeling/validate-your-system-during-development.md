---
title: Validar el sistema durante el desarrollo
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 328b600a21adf274d1d016f595438eb5622ee853
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663746"
---
# <a name="validate-your-system-during-development"></a>Validar el sistema durante el desarrollo

Visual Studio puede ayudarle a mantener el software coherente con los requisitos del usuario y con la arquitectura del sistema.

Para ver las versiones de Visual Studio compatibles con cada característica, consulte [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Tareas clave

Use las tareas siguientes para validar el software:

|**Tareas**|**Temas relacionados**|
|-|-|
|**Asegúrese de que el software cumple los requisitos de los usuarios**:<br /><br />Use los requisitos y los modelos arquitectónicos para ayudarle a organizar las pruebas del sistema y sus componentes. Con esta práctica, tendrá la certeza de que incluye en la prueba los requisitos que son importantes para los usuarios y otras partes interesadas, y podrá actualizar las pruebas rápidamente cuando cambien los requisitos.|- [desarrollar pruebas a partir de un modelo](../modeling/develop-tests-from-a-model.md)|
|**Asegúrese de que el software mantiene la coherencia con el diseño previsto del sistema:**<br /><br />Los diagramas de dependencia describen las dependencias prepensadas entre los componentes de la aplicación. Durante el desarrollo, puede comprobar si las dependencias reales del código se ajustan al diseño previsto.|- [crear diagramas de dependencia del código](../modeling/create-layer-diagrams-from-your-code.md)<br />- [validar el código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Recursos externos

|**Categoría**|**Links**|
|-|-|
|**Vídeos**|![link al vídeo ](../data-tools/media/playvideo.gif) [Channel 9: Doug siete: Descripción del código y diseño de sistemas con Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![link al vídeo ](../data-tools/media/playvideo.gif) [Channel 9: diseño de una aplicación](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-5-architecting-an-application))|
|**Foros**|- [Herramientas de visualización y modelado de Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />extensibilidad de - [Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)|

## <a name="see-also"></a>Vea también

- [Requisitos del usuario de modelos](../modeling/model-user-requirements.md)
- [Analizar y modelar la arquitectura](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
