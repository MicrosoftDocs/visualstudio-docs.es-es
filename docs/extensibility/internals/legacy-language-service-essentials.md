---
title: "Fundamentos de servicio de lenguaje heredado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "idiomas, integrar en Visual Studio"
  - "Servicios de lenguaje, integración de lenguajes de programación"
  - "Visual Studio, la integración de lenguajes de programación"
  - "lenguajes de programación, integrar en Visual Studio"
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Fundamentos de servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Debe proporcionar un servicio de lenguaje para integrar un lenguaje de programación en Visual Studio. Este tema explica las características disponibles en los servicios de lenguaje heredado.  
  
 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la nueva forma de implementar las características del servicio de lenguaje es usar extensiones MEF. Para obtener más información acerca de la nueva forma de implementar un servicio de lenguaje, consulte [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Se recomienda que comience a utilizar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
 Servicios de lenguaje heredado proporcionan las siguientes características:  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Seleccionar el color de la sintaxis|Hace que la vista del editor mostrar diferentes colores y estilos de fuente para los distintos elementos de un idioma. Esta diferenciación resultará más fácil de leer y editar archivos.<br /><br /> Para obtener información general, consulte [Colores en un servicio de lenguaje heredado de sintaxis](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Para obtener información sobre esta característica en el marco de trabajo de paquete administrado \(MPF\), consulte [Coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|  
|Instrucciones completadas|Completa una instrucción o palabra clave que el usuario ha empezado a escribir. Finalización de instrucciones ayuda a los usuarios especificar instrucciones difíciles más fácilmente, con menos posibilidades de error y escribir menos.<br /><br /> Para obtener información general, consulte [Finalización de instrucciones en un servicio de lenguaje heredado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Para obtener información sobre esta característica en la MPF, consulte [Finalización de palabras en un servicio de lenguaje heredado](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|  
|Coincidencia de llaves|Información destacada de pares de caracteres, como llaves. Cuando el usuario escribe un carácter de cierre como "}", coincidencia de llaves resalta el correspondiente carácter de apertura, como "{". Cuando hay varios niveles de caracteres de cierre, esta característica ayuda a los usuarios confirmar que los caracteres están emparejados correctamente.<br /><br /> Para obtener información sobre esta característica en la MPF, consulte [Coincidencia de llaves en un servicio de lenguaje heredado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|  
|Información sobre herramientas de información de parámetro|Muestra una lista de posibles firmas del método sobrecargado que el usuario está escribiendo actualmente.<br /><br /> Para obtener información general, consulte [Información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Para obtener información sobre esta característica en la MPF, consulte [Información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|  
|Marcadores de error|Muestra un subrayado ondulado rojo, también conocido como un subrayado, debajo del texto es sintácticamente incorrecta. Marcadores de error normalmente se utilizan para comunicar a los usuarios de las palabras clave mal escritas, sin cerrar paréntesis, caracteres no válidos y errores similares.<br /><br /> En las clases MPF, marcadores de error se controlan automáticamente en el <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> método de la <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase.|  
  
 Muchas de estas características requieren el servicio de lenguaje para analizar código fuente. A menudo se pueden reutilizar el encadenamiento y analizar el código para el compilador o intérprete.  
  
 Las siguientes características relacionadas con la compatibilidad con lenguajes de programación, pero no forman parte de los servicios de lenguaje:  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Evaluadores de expresión|Admite la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador validando los puntos de interrupción y proporcionar una lista de expresiones que se mostrará en el **automático** ventana de depuración.<br /><br /> Para obtener más información, consulta [Soporte técnico de servicio de lenguaje para la depuración](../../extensibility/internals/language-service-support-for-debugging.md).|  
|Herramientas de exploración de símbolos|Admite **Examinador de objetos**, **vista de clases**, **Examinador de llamadas**, y **Buscar símbolo resultados**.|