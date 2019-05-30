---
title: Extensibilidad de servicio de lenguaje heredado | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14bee804d532138ddf5c9b63039f4bfb8abbe02c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344842"
---
# <a name="legacy-language-service-extensibility"></a>Extensibilidad de servicio de lenguaje heredado
Un servicio de lenguaje proporciona compatibilidad específica del lenguaje para editar código fuente en el IDE.

 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características de servicio de lenguaje es usar las extensiones MEF. Para obtener más información acerca de la nueva forma de implementar un servicio de lenguaje, consulte [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).

 Esta sección describe la estructura y la implementación de un servicio de lenguaje heredado.

## <a name="in-this-section"></a>En esta sección
- [Migración de un servicio de lenguaje heredado](../../extensibility/internals/migrating-a-legacy-language-service.md)

 Explica cómo actualizar un servicio de lenguaje de Visual Studio 2008 para la versión más reciente.

- [Fundamentos de servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-essentials.md)

 Proporciona información importante sobre cómo desarrollar servicios de lenguaje para integrar un lenguaje de programación en Visual Studio.

- [Desarrollo de un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)

 Proporciona vínculos a temas que pueden ayudarle a crear un servicio de lenguaje.

- [Colores de la sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Proporciona información sobre la compatibilidad con resaltado de sintaxis en un servicio de lenguaje.

- [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Proporciona información sobre cómo usar managed package framework (MPF) para implementar un servicio de lenguaje completo en código administrado.

- [Compatibilidad con herramientas de exploración de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Describe las bibliotecas y herramientas que permiten examinar vistas de árbol de símbolos en el IDE.

## <a name="related-sections"></a>Secciones relacionadas
- [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md)

 Proporciona información general de los editores de Visual Studio.

- [Compatibilidad del servicio de lenguaje para la depuración](../../extensibility/internals/language-service-support-for-debugging.md)

 Proporciona información acerca de y un vínculo a la depuración de SDK de Visual Studio, que contiene la información necesaria para crear y personalizar los componentes del depurador para depurar programas.