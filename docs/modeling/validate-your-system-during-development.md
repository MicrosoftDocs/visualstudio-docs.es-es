---
title: Validar el sistema durante el desarrollo
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9fb9810f1c212dfb881f5725676a79c6307b9cfa
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476501"
---
# <a name="validate-your-system-during-development"></a>Validar el sistema durante el desarrollo

Visual Studio puede ayudar a mantener la coherencia con los requisitos de usuario y la arquitectura del sistema de su software.

Para ver las versiones de Visual Studio compatibles con cada característica, consulte [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Tareas clave

Use las siguientes tareas para validar el software:

|**Tareas**|**Temas relacionados**|
|-|-|
|**Asegúrese de que el software cumple los requisitos de los usuarios**:<br /><br />Use los requisitos y los modelos arquitectónicos para ayudarle a organizar las pruebas del sistema y sus componentes. Con esta práctica, tendrá la certeza de que incluye en la prueba los requisitos que son importantes para los usuarios y otras partes interesadas, y podrá actualizar las pruebas rápidamente cuando cambien los requisitos.|- [Desarrollar pruebas en un modelo](../modeling/develop-tests-from-a-model.md)|
|**Asegúrese de que el software mantiene la coherencia con el diseño previsto del sistema:**<br /><br />Diagramas de dependencia describen las dependencias previstas entre los componentes de la aplicación. Durante el desarrollo, puede comprobar si las dependencias reales del código se ajustan al diseño previsto.|- [Crear diagramas de dependencia desde el código](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Validar código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Recursos externos

|**Categoría**|**Vínculos**|
|-|-|
|**Vídeos**|![vínculo a vídeo](../data-tools/media/playvideo.gif) [Channel 9: Doug Seven: Comprensión del código y diseño de sistemas con Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![vínculo a vídeo](../data-tools/media/playvideo.gif) [Channel 9: Diseñar una aplicación](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-5-architecting-an-application))|
|**Foros**|- [Herramientas de visualización y modelado de Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Extensibilidad de Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)|

## <a name="see-also"></a>Vea también

- [Requisitos del usuario de modelos](../modeling/model-user-requirements.md)
- [Analizar y modelar la arquitectura](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
