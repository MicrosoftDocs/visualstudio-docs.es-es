---
title: Imprescindibles del servicio de idiomas heredados Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 501bccf755293e86e8a9dc23fce125a10c882376
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707423"
---
# <a name="legacy-language-service-essentials"></a>Fundamentos de servicio de lenguaje heredado
Debe proporcionar un servicio de lenguaje para integrar un lenguaje de programación en Visual Studio. En este tema se explican las características disponibles en los servicios de lenguaje heredado.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar características de servicio de lenguaje es usar extensiones MEF. Para obtener más información sobre la nueva forma de implementar un servicio de lenguaje, vea [Extensiones](../../extensibility/editor-and-language-service-extensions.md)de servicio de editor y lenguaje .

> [!NOTE]
> Le recomendamos que comience a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

 Los servicios de lenguaje heredados proporcionan las siguientes características:

|Característica|Descripción|
|-------------|-----------------|
|Seleccionar el color de la sintaxis|Hace que la vista del editor muestre diferentes colores y estilos de fuente para los diferentes elementos de un idioma. Esta diferenciación puede facilitar la lectura y edición de archivos.<br /><br /> Para obtener información general, consulte [Coloración](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)de sintaxis en un servicio de lenguaje heredado .<br /><br /> Para obtener información sobre esta característica en el marco de trabajo de paquete administrado (MPF), vea [Colorear sintaxis en un servicio](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)de lenguaje heredado .|
|Instrucciones completadas|Completa una instrucción o palabra clave que el usuario ha comenzado a escribir. La finalización de instrucciones ayuda a los usuarios a introducir instrucciones difíciles más fácilmente, con menos escritura y menos posibilidades de error.<br /><br /> Para obtener información general, vea [Finalización](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)de instrucciones en un servicio de lenguaje heredado .<br /><br /> Para obtener información acerca de esta característica en el MPF, vea [Finalización](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)de Word en un servicio de lenguaje heredado .|
|Coincidencia de llaves|Resalta los caracteres emparejados, como llaves. Cuando el usuario escribe un carácter de cierre, como por ejemplo, "-", la coincidencia de llaves resalta el carácter de apertura correspondiente, como, por ejemplo, ". Cuando hay varios niveles de caracteres envolventes, esta característica ayuda a los usuarios a confirmar que los caracteres envolventes están emparejados correctamente.<br /><br /> Para obtener información sobre esta característica en el MPF, vea [Coincidencia de llaves en un servicio](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)de lenguaje heredado .|
|Información sobre parámetros sobre herramientas|Muestra una lista de posibles firmas para el método sobrecargado que el usuario está escribiendo actualmente.<br /><br /> Para obtener información general, consulte [Información de parámetros en un servicio](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)de lenguaje heredado .<br /><br /> Para obtener información sobre esta característica en el MPF, consulte [Información de parámetros en un servicio](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)de lenguaje heredado .|
|Marcadores de error|Muestra un subrayado rojo ondulado, también conocido como ondulado, debajo del texto que es sintácticamente incorrecto. Los marcadores de error suelen utilizarse para dar a conocer a los usuarios palabras clave mal escritas, paréntesis no cerrados, caracteres no válidos y errores similares.<br /><br /> En las clases MPF, los marcadores de error se controlan automáticamente en el <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> método de la <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase.|

 Muchas de estas características requieren que el servicio de lenguaje analice el código fuente. A menudo puede reutilizar el código de tokenización y análisis para el compilador o intérprete.

 Las siguientes características están relacionadas con la compatibilidad con lenguajes de programación, pero no forman parte de los servicios de lenguaje:

| Característica | Descripción |
|-----------------------| - |
| Evaluadores de expresiones | Admite [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el depurador validando puntos de interrupción y proporcionando una lista de expresiones que se mostrarán en la ventana de depuración **Autos.**<br /><br /> Para obtener más información, vea Compatibilidad del servicio de [lenguaje para la depuración](../../extensibility/internals/language-service-support-for-debugging.md). |
| Herramientas de exploración de símbolos | Soporta **Examinador de objetos**, Vista de **clases**, **Navegador de llamadas**y **Buscar resultados de símbolos**. |
