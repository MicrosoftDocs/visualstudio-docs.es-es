---
title: Características del servicio de lenguaje heredado2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], code development aides
ms.assetid: 97c38622-ae0b-4ae0-90ed-604072c298d3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33f12e816476aa54f334988b99b9e86e820784f6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707371"
---
# <a name="legacy-language-service-features"></a>Características del servicio de lenguaje heredado
En los temas siguientes se enumeran algunas de las características del servicio de lenguaje heredado que puede proporcionar.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar características de servicio de lenguaje es usar extensiones MEF. Para obtener más información sobre la nueva forma de implementar un servicio de lenguaje, vea [Extensiones](../../extensibility/editor-and-language-service-extensions.md)de servicio de editor y lenguaje .

> [!NOTE]
> Le recomendamos que comience a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="in-this-section"></a>En esta sección
- [Colores de la sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Explica cómo implementar el color de sintaxis.

- [Formato automático en un servicio de lenguaje heredado](../../extensibility/internals/automatic-formatting-in-a-legacy-language-service.md)

 Explica cómo implementar el formato automático.

- [Información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Explica cómo implementar la información sobre herramientas de parámetros de IntelliSense.

- [Finalización de instrucciones en un servicio de lenguaje heredado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Explica cómo implementar la lista de instrucciones de IntelliSense y la lista de finalización de miembros.

- [Esquematización y texto oculto en un servicio de lenguaje heredado](../../extensibility/internals/outlining-and-hidden-text-in-a-legacy-language-service.md)

 Explica cómo implementar la esquematización u texto oculto.

- [Provisión de compatibilidad con esquematización ampliada en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Explica algunos de los pasos para implementar la compatibilidad con el depurador.

## <a name="related-sections"></a>Secciones relacionadas
