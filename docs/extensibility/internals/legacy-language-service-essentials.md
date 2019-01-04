---
title: Conceptos básicos del servicio de lenguaje heredado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 79ecbd971315c004a9be40221a6950afb5856823
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53847209"
---
# <a name="legacy-language-service-essentials"></a>Fundamentos de servicio de lenguaje heredado
Debe proporcionar un servicio de lenguaje para integrar un lenguaje de programación en Visual Studio. En este tema se explica las características disponibles en los servicios de lenguaje heredado.  

 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características de servicio de lenguaje es usar las extensiones MEF. Para obtener más información acerca de la nueva forma de implementar un servicio de lenguaje, consulte [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).  

> [!NOTE]
>  Se recomienda que comience a usar el nuevo editor de API tan pronto como sea posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  

 Servicios de lenguaje heredado proporcionan las siguientes características:  

|Característica|Descripción|  
|-------------|-----------------|  
|Seleccionar el color de la sintaxis|Hace que la vista del editor mostrar diferentes colores y estilos de fuente para los distintos elementos de un idioma. Esta diferenciación puede hacer más fácil de leer y editar archivos.<br /><br /> Para obtener información general, consulte [colores de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Para obtener información sobre esta característica en managed package framework (MPF), consulte [coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|  
|Finalización de instrucciones|Completa una instrucción o palabra clave que el usuario ha empezado a escribir. Finalización de instrucciones ayuda a los usuarios especificar instrucciones difíciles más fácilmente, con menos posibilidades de error y escribir menos.<br /><br /> Para obtener información general, consulte [finalización de instrucciones en un servicio de lenguaje heredado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Para obtener información sobre esta característica en MPF, vea [finalización de palabras en un servicio de lenguaje heredado](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|  
|Coincidencia de llaves|Información destacada de pares de caracteres, como las llaves. Cuando el usuario escribe un carácter de cierre, como "}", coincidencia de llaves resalta los correspondientes caracteres, de apertura, como "{". Cuando hay varios niveles de caracteres de cierre, esta característica ayuda a los usuarios confirmar que los caracteres de inclusión están emparejados correctamente.<br /><br /> Para obtener información sobre esta característica en MPF, vea [coincidencia de llaves en un servicio de lenguaje heredado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|  
|Información sobre herramientas de información de parámetro|Muestra una lista de las firmas posibles para el método sobrecargado que el usuario está escribiendo actualmente.<br /><br /> Para obtener información general, consulte [información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Para obtener información sobre esta característica en MPF, vea [información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|  
|Marcadores de error|Muestra un subrayado rojo ondulado, también conocido como un subrayado, bajo el texto que no es sintácticamente correcto. Los marcadores de error normalmente se usan para que los usuarios sea consciente de los paréntesis sin cerrar, palabras clave mal escritas, caracteres no válidos y errores similares.<br /><br /> En las clases MPF, marcadores de errores se controlan automáticamente en el <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> método de la <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase.|  

 Muchas de estas características requieren que el servicio de lenguaje para analizar código fuente. A menudo se pueden reutilizar el encadenamiento y el análisis de código para el compilador o intérprete.  

 Las siguientes características están relacionadas con compatibilidad con lenguajes de programación, pero no forman parte de los servicios de lenguaje:  


| Característica | Descripción |
|-----------------------| - |
| Evaluadores de expresión | Admite la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador mediante la validación de los puntos de interrupción y proporcionar una lista de expresiones que se mostrará en el **automático** ventana de depuración.<br /><br /> Para obtener más información, consulte [soporte técnico de servicio de lenguaje para depuración](../../extensibility/internals/language-service-support-for-debugging.md). |
| Herramientas de exploración de símbolos | Admite **Examinador de objetos**, **vista de clases**, **Explorador de llamadas**, y **Buscar símbolo resultados**. |
