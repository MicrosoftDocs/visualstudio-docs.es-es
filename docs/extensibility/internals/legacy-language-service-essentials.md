---
title: Conceptos básicos del servicio de lenguaje heredado | Microsoft Docs
description: Obtenga información sobre las características esenciales disponibles en los servicios de lenguaje heredados que le permiten integrar un lenguaje de programación en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fa3fc358e7557360f02a80f108bcbec74ae48e5f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074566"
---
# <a name="legacy-language-service-essentials"></a>Fundamentos de servicio de lenguaje heredado
Debe proporcionar un servicio de lenguaje para integrar un lenguaje de programación en Visual Studio. En este tema se explican las características disponibles en los servicios de lenguaje heredado.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar las características del servicio de lenguaje es usar extensiones de MEF. Para obtener más información sobre la nueva manera de implementar un servicio de lenguaje, vea [Editor y extensiones del servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Le recomendamos que empiece a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento del servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

 Los servicios de lenguaje heredados proporcionan las siguientes características:

|Característica|Descripción|
|-------------|-----------------|
|Seleccionar el color de la sintaxis|Hace que la vista del editor muestre diferentes colores y estilos de fuente para los distintos elementos de un idioma. Esta diferenciación puede facilitar la lectura y la edición de archivos.<br /><br /> Para obtener información general, consulte [color de la sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Para obtener información acerca de esta característica en Managed Package Framework (MPF), consulte [coloración de la sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|
|Instrucciones completadas|Completa una instrucción o palabra clave que el usuario ha empezado a escribir. La finalización de instrucciones ayuda a los usuarios a escribir declaraciones difíciles más fácilmente, con menos tipos y menos posibilidades de error.<br /><br /> Para obtener información general, consulte [finalización de instrucciones en un servicio de lenguaje heredado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Para obtener información acerca de esta característica en MPF, consulte [finalización de palabras en un servicio de lenguaje heredado](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|
|Coincidencia de llaves|Resalta los caracteres emparejados, como las llaves. Cuando el usuario escribe un carácter de cierre como "}", la coincidencia de llaves resalta el carácter de apertura correspondiente, como "{". Cuando hay varios niveles de caracteres envolventes, esta característica ayuda a los usuarios a confirmar que los caracteres envolventes se emparejan correctamente.<br /><br /> Para obtener información sobre esta característica en MPF, consulte [coincidencia de llaves en un servicio de lenguaje heredado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|
|Información sobre parámetros, información sobre herramientas|Muestra una lista de posibles firmas para el método sobrecargado que el usuario está escribiendo actualmente.<br /><br /> Para obtener información general, consulte [información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Para obtener información sobre esta característica en MPF, consulte [información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|
|Marcadores de error|Muestra un subrayado rojo ondulado, también conocido como ondulado, en texto que es sintácticamente incorrecto. Normalmente, los marcadores de error se usan para que los usuarios conozcan palabras clave mal escritas, paréntesis sin cerrar, caracteres no válidos y errores similares.<br /><br /> En las clases MPF, los marcadores de error se administran automáticamente en el <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> método de la <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase.|

 Muchas de estas características requieren que el servicio de lenguaje analice el código fuente. A menudo, puede reutilizar el código de tokens y análisis para el compilador o el intérprete.

 Las siguientes características están relacionadas con la compatibilidad con los lenguajes de programación pero no forman parte de los servicios de lenguaje:

| Característica | Descripción |
|-----------------------| - |
| Evaluadores de expresiones | Admite el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador validando los puntos de interrupción y proporcionando una lista de expresiones que se mostrarán en la ventana depuración **automática** .<br /><br /> Para obtener más información, vea [compatibilidad del servicio de lenguaje para la depuración](../../extensibility/internals/language-service-support-for-debugging.md). |
| Herramientas de exploración de símbolos | Admite **Examinador de objetos**, **vista de clases**, **Explorador de llamadas** y **Buscar resultados de símbolos**. |
