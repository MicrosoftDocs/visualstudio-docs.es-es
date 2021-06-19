---
title: Validar el sistema durante el desarrollo
description: Obtenga información sobre Visual Studio puede ayudar a mantener el software coherente con los requisitos del usuario y con la arquitectura del sistema.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ae85c7f98aab3e852a810976cc1cecbd83b65307
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388378"
---
# <a name="validate-your-system-during-development"></a>Validar el sistema durante el desarrollo

Visual Studio puede ayudar a mantener el software coherente con los requisitos del usuario y con la arquitectura del sistema.

Para ver las versiones de Visual Studio compatibles con cada característica, consulte [Version support for architecture and modeling tools](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

## <a name="key-tasks"></a>Tareas clave

Use las siguientes tareas para validar el software:

|**Tareas**|**Temas relacionados**|
|-|-|
|**Asegúrese de que el software cumple los requisitos de los usuarios**:<br /><br />Use los requisitos y los modelos arquitectónicos para ayudarle a organizar las pruebas del sistema y sus componentes. Con esta práctica, tendrá la certeza de que incluye en la prueba los requisitos que son importantes para los usuarios y otras partes interesadas, y podrá actualizar las pruebas rápidamente cuando cambien los requisitos.|- [Desarrollo de pruebas a partir de un modelo](../modeling/develop-tests-from-a-model.md)|
|**Asegúrese de que el software mantiene la coherencia con el diseño previsto del sistema:**<br /><br />Los diagramas de dependencias describen las dependencias previstas entre los componentes de la aplicación. Durante el desarrollo, puede comprobar si las dependencias reales del código se ajustan al diseño previsto.|- [Creación de diagramas de dependencia a partir del código](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Validación de código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Recursos externos

|**Categoría**|**Vínculos**|
|-|-|
|**Vídeos**|![vínculo al vídeo ](../data-tools/media/playvideo.gif) [Channel 9: Doug Seven: Code Understanding and Systems Design with Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![vínculo al vídeo ](../data-tools/media/playvideo.gif) [Channel 9: Architecting an Application](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-5-architecting-an-application))|
|**Foros**|- [Herramientas de visualización y modelado de Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Visual Studio extensibilidad](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)|

## <a name="see-also"></a>Vea también

- [Requisitos del usuario de modelos](../modeling/model-user-requirements.md)
- [Analizar y modelar la arquitectura](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
