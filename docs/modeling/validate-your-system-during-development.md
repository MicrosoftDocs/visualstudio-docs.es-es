---
title: Validar el sistema durante el desarrollo
description: Obtenga información sobre cómo Visual Studio puede ayudar a mantener su software coherente con los requisitos del usuario y con la arquitectura del sistema.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a803b2fb7eb7c682e29ae0d17698ef673927d751
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361409"
---
# <a name="validate-your-system-during-development"></a>Validar el sistema durante el desarrollo

Visual Studio puede ayudarle a mantener el software coherente con los requisitos del usuario y con la arquitectura del sistema.

Para ver las versiones de Visual Studio compatibles con cada característica, consulte [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Tareas clave

Use las tareas siguientes para validar el software:

|**Tareas**|**Temas relacionados**|
|-|-|
|**Asegúrese de que el software cumple los requisitos de los usuarios**:<br /><br />Use los requisitos y los modelos arquitectónicos para ayudarle a organizar las pruebas del sistema y sus componentes. Con esta práctica, tendrá la certeza de que incluye en la prueba los requisitos que son importantes para los usuarios y otras partes interesadas, y podrá actualizar las pruebas rápidamente cuando cambien los requisitos.|- [Desarrollar pruebas a partir de un modelo](../modeling/develop-tests-from-a-model.md)|
|**Asegúrese de que el software mantiene la coherencia con el diseño previsto del sistema:**<br /><br />Los diagramas de dependencia describen las dependencias prepensadas entre los componentes de la aplicación. Durante el desarrollo, puede comprobar si las dependencias reales del código se ajustan al diseño previsto.|- [Creación de diagramas de dependencia a partir del código](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Validación de código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Recursos externos

|**Categoría**|**Vínculos**|
|-|-|
|**Vídeos**|![vínculo al canal de vídeo ](../data-tools/media/playvideo.gif) [9: Doug siete: comprensión del código y diseño del sistema con Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![vínculo al canal de vídeo ](../data-tools/media/playvideo.gif) [9: diseño de una aplicación](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-5-architecting-an-application)|
|**Foros**|- [Herramientas de visualización y modelado de Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Extensibilidad de Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)|

## <a name="see-also"></a>Consulta también

- [Requisitos del usuario de modelos](../modeling/model-user-requirements.md)
- [Analizar y modelar la arquitectura](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
