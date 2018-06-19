---
title: Essentials de servicio de lenguaje heredado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 68b92b821ad77b050ad2116da6fd930b975dad5a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135450"
---
# <a name="legacy-language-service-essentials"></a>Essentials de servicio de lenguaje heredado
Debe proporcionar un servicio de lenguaje para integrar un lenguaje de programación en Visual Studio. En este tema se explica las características disponibles en los servicios de lenguaje heredado.  
  
 Los servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características del servicio de lenguaje es utilizar las extensiones MEF. Para obtener más información acerca de la nueva forma de implementar un servicio de lenguaje, consulte [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Le recomendamos que empiece a usar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
 Servicios de lenguaje heredado proporcionan las siguientes características:  
  
|Característica|Descripción|  
|-------------|-----------------|  
|Seleccionar el color de la sintaxis|Hace que la vista del editor mostrar diferentes colores y estilos de fuente para los distintos elementos de un idioma. Esta diferencia puede resulte más fácil leer y editar archivos.<br /><br /> Para obtener información general, vea [colores de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Para obtener información acerca de esta característica en managed package framework (MPF), consulte [coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|  
|Finalización de instrucciones|Completa una instrucción o palabra clave que el usuario ha empezado a escribir. Finalización de instrucciones ayuda a los usuarios escribir instrucciones difíciles más fácilmente y con menos posibilidades de error y escribir menos.<br /><br /> Para obtener información general, vea [finalización de instrucciones en un servicio de lenguaje heredado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Para obtener información sobre esta característica MPF, vea [palabra completa en un servicio de lenguaje heredado](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|  
|Coincidencia de llaves|Aspectos destacados emparejan caracteres como llaves. Cuando el usuario escribe un carácter de cierre como "}", la coincidencia de llaves resalta los correspondientes caracteres, de apertura, como "{". Cuando hay varios niveles de caracteres de cierre, esta característica ayuda a los usuarios confirmar que los caracteres de inclusión están emparejados correctamente.<br /><br /> Para obtener información sobre esta característica MPF, vea [la coincidencia de llaves en un servicio de lenguaje heredado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|  
|Información sobre herramientas de información de parámetro|Muestra una lista de posibles firmas del método sobrecargado que actualmente está escribiendo el usuario.<br /><br /> Para obtener información general, vea [información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Para obtener información sobre esta característica MPF, vea [información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|  
|Marcadores de error|Muestra un subrayado rojo ondulado, también conocido como un onduladas, bajo el texto que no es sintácticamente correcta. Marcadores de error normalmente se usan para hacer que los usuarios sea consciente de las palabras clave mal escritas, paréntesis sin cerrar, caracteres no válidos y errores similares.<br /><br /> En las clases MPF, marcadores de error se administran automáticamente en el <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> método de la <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase.|  
  
 Muchas de estas características requieren el servicio de lenguaje para analizar el código fuente. A menudo, puede reutilizar el encadenamiento y analizar el código para el compilador o intérprete.  
  
 Las siguientes características relacionadas con la compatibilidad con lenguajes de programación, pero no forman parte de servicios de lenguaje:  
  
|Característica|Descripción|  
|-------------|-----------------|  
|Evaluadores de expresión|Admite la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador validando los puntos de interrupción y proporcionar una lista de expresiones que se mostrará en el **automático** ventana de depuración.<br /><br /> Para obtener más información, consulte [compatibilidad de servicio de lenguaje para depuración](../../extensibility/internals/language-service-support-for-debugging.md).|  
|Herramientas de exploración de símbolos|Admite **Examinador de objetos**, **vista de clases**, **Explorador de llamadas**, y **Buscar símbolo resultados**.|