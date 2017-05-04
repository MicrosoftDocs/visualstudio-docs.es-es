---
title: "Comprobar y depurar c&#243;digo de SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "pruebas unitarias [desarrollo de SharePoint en Visual Studio]"
  - "IntelliTrace [desarrollo de SharePoint en Visual Studio]"
  - "Desarrollo de SharePoint en Visual Studio, IntelliTrace"
  - "Desarrollo de SharePoint en Visual Studio, pruebas unitarias"
ms.assetid: b5f3bce2-6a51-41b1-a292-9e384bae420c
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Comprobar y depurar c&#243;digo de SharePoint
  Con IntelliTrace y las pruebas unitarias, puede depurar las soluciones de SharePoint más fácilmente y asegurarse de que cada método en ellas funciona correctamente.  Puede usar estas características para los proyectos de SharePoint en [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] siguiendo los mismos procedimientos que en otros tipos de proyectos.  
  
## IntelliTrace  
 Mediante IntelliTrace, puede determinar el estado actual de la solución de SharePoint, así como los eventos que se produjeron en el pasado y el contexto en el que se produjeron.  Puede navegar hacia delante y hacia atrás a varios puntos de la solución de SharePoint donde se grabaron eventos de interés y revisar los estados y valores de las variables en cada punto.  Mediante esta navegación dinámica, puede depurar de forma más rápida y fácil las soluciones de SharePoint sin tener que establecer numerosos puntos de interrupción.  También puede guardar la sesión de depuración en un archivo de registro de IntelliTrace \(.iTrace\), abrirlo posteriormente en Visual Studio Ultimate y realizar la depuración posterior a un bloqueo.  El archivo .iTrace incluye información detallada sobre cuándo y dónde se produjeron los errores específicos de SharePoint, de modo que es más fácil averiguar qué produce esos errores.  La información del archivo .iTrace es un subconjunto del registro de errores completo que crea el sistema de registro unificado \(ULS\) en SharePoint.  Esta información incluye eventos que son específicos de SharePoint, como cuando un perfil de usuario se abre o se cierra y cuando las propiedades de un proyecto de SharePoint se cargan, se leen o se cambian.  Puede configurar los eventos que registra IntelliTrace.  Para obtener más información, vea [Uso de datos de IntelliTrace guardados](../debugger/using-saved-intellitrace-data.md) y [Configurar IntelliTrace para recopilar información de depuración](http://msdn.microsoft.com/es-es/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
 Cuando se produce un error en SharePoint, el cuadro de diálogo de error muestra un identificador "identificador de correlación" para ese error concreto.  También puede obtener identificador de correlación de los eventos enumerados en el archivo .iTrace.  Para mostrar una lista de todos los eventos que se produjeron con un identificador de correlación determinado, puede escribir el identificador en la sección **Análisis** de la página de resumen de IntelliTrace.  En esa sección, puede elegir si se muestran solo los nombres de los eventos que se produjeron o los nombres de los eventos junto con su información de llamadas, como el nombre de función, los puntos de salida y de entrada, los parámetros y los valores devueltos.  
  
 Puede recopilar eventos de Visual Studio en IntelliTrace eligiendo la tecla **F5**.  Sin embargo, para obtener los eventos que son específicos de SharePoint, debe reunir los datos de IntelliTrace en las soluciones de SharePoint mediante Microsoft Monitoring Agent.  Esta herramienta recopila datos de IntelliTrace y crea archivos .iTrace para las aplicaciones que se implementan fuera de Visual Studio.  Para obtener más información, vea [Características de IntelliTrace](../debugger/intellitrace-features.md) y [Usar el recopilador independiente de IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
## Pruebas unitarias  
 Puede encontrar más fácilmente los errores en el código si realiza pruebas unitarias, en las que el código de prueba se escribe y ejecuta en los métodos de prueba.  Estos métodos contienen variables vacías y una instrucción Assert que puede usar para comprobar la lógica y funcionalidad del proyecto basándose en el modelo de objetos de SharePoint.  Para obtener más información, vea [Haga una prueba unitaria de su código](../test/unit-test-your-code.md).  
  
### Compatibilidad con el marco Microsoft Fakes  
 Los proyectos de SharePoint admiten Microsoft Fakes, un marco de aislamiento en el que se pueden crear códigos auxiliares basados en el delegado y en correcciones de compatibilidad \(shim\) en las aplicaciones basadas en .NET Framework.  Utilizando el marco Fakes, puede crear, mantener e insertar implementaciones ficticias en las pruebas unitarias.  Estos códigos auxiliares y shims aíslan las pruebas unitarias del entorno.  Puede crear códigos auxiliares para probar código que utiliza interfaces o clases no selladas con métodos reemplazables.  Puede crear shims para redirigir llamadas codificadas para clases selladas con métodos estáticos o que no se pueden reemplazar a una implementación alternativa de shim.  También puede usar delegados con tipos de código auxiliar y tipos de shim para personalizar dinámicamente el comportamiento de los miembros individuales del código auxiliar.  Para obtener más información, vea [Aislar el código probado con Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Uso de IntelliTrace](../debugger/intellitrace.md)|Describe cómo depurar soluciones de Visual Studio más fácilmente mediante IntelliTrace.|  
|[Tutorial: Depurar una aplicación de SharePoint mediante IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|Muestra cómo buscar los errores de codificación en un proyecto de SharePoint mediante IntelliTrace.|  
|[Haga una prueba unitaria de su código](../test/unit-test-your-code.md)|Describe cómo buscar errores lógicos en el código mediante pruebas unitarias.|  
  
## Vea también  
 [Mejorar la calidad del código](../test/improve-code-quality.md)  
  
  