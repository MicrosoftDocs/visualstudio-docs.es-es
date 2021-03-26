---
title: Features2 de servicio de lenguaje heredado | Microsoft Docs
description: Obtenga información sobre algunas de las características del servicio de lenguaje heredado que puede proporcionar mediante el uso de extensiones de Managed Extensibility Framework (MEF) en el SDK de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], code development aides
ms.assetid: 97c38622-ae0b-4ae0-90ed-604072c298d3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a12ee207f7fb7e4f4e2d202d5d63d468e9cea547
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074488"
---
# <a name="legacy-language-service-features-2"></a>Características del servicio de lenguaje heredado 2
En los temas siguientes se enumeran algunas de las características del servicio de lenguaje heredado que puede proporcionar.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar las características del servicio de lenguaje es usar extensiones de MEF. Para obtener más información sobre la nueva manera de implementar un servicio de lenguaje, vea [Editor y extensiones del servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Le recomendamos que empiece a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento del servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="in-this-section"></a>En esta sección
- [Colores de la sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Explica cómo implementar el color de la sintaxis.

- [Formato automático en un servicio de lenguaje heredado](../../extensibility/internals/automatic-formatting-in-a-legacy-language-service.md)

 Explica cómo implementar el formato automático.

- [Información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Explica cómo implementar la información sobre herramientas de información de parámetros de IntelliSense.

- [Finalización de instrucciones en un servicio de lenguaje heredado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Explica cómo implementar la lista de instrucciones de IntelliSense y la lista de finalización de miembros.

- [Esquematización y texto oculto en un servicio de lenguaje heredado](../../extensibility/internals/outlining-and-hidden-text-in-a-legacy-language-service.md)

 Explica cómo implementar la esquematización o el texto oculto.

- [Provisión de compatibilidad con esquematización ampliada en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Explica algunos de los pasos necesarios para implementar la compatibilidad del depurador.

## <a name="related-sections"></a>Secciones relacionadas
