---
title: "Generar perfiles de rendimiento de aplicaciones de SharePoint"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Profiling.SilverlightWebPartOnly"
  - "VS.SharePointTools.Profiling.DotNetTrustLevel"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "pruebas de rendimiento [desarrollo de SharePoint en Visual Studio]"
  - "generación de perfiles [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, pruebas de rendimiento"
  - "desarrollo de SharePoint en Visual Studio, generación de perfiles"
ms.assetid: 61ae02e7-3f37-4230-bae1-54a498c2fae8
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Generar perfiles de rendimiento de aplicaciones de SharePoint
  Si las aplicaciones de SharePoint funcionan despacio o de forma ineficaz, puede utilizar las características de generación de perfiles de Visual Studio para identificar código problemático y otros elementos.  Usando la característica de prueba de carga, puede determinar el rendimiento de una aplicación de SharePoint bajo estrés, como cuando muchos usuarios tienen acceso a la aplicación simultáneamente.  Si ejecuta pruebas de rendimiento web, puede medir el rendimiento de la aplicación en web.  Mediante el uso de pruebas de IU codificadas, puede comprobar si funciona correctamente toda la aplicación de SharePoint, incluida la interfaz de usuario.  Cuando se usan estas pruebas juntas, pueden ayudarle a identificar problemas de rendimiento antes de implementar la aplicación.  
  
## Información general sobre las Herramientas de generación de perfiles  
 La generación de perfiles hace referencia al proceso de observar y grabar el comportamiento de rendimiento de la aplicación mientras se ejecuta.  Mediante la generación de perfiles para la aplicación, puede detectar problemas tales como cuellos de botella, código ineficaz y problemas de asignación de memoria, que provocan que las aplicaciones se ejecuten con lentitud o utilicen demasiada memoria.  Por ejemplo, puede utilizar la generación de perfiles para identificar zonas activas en el código, que son los segmentos de código a los que se llama con frecuencia y que pueden ralentizar el rendimiento general de la aplicación.  Después de identificar las zonas activas, puede optimizarlas con frecuencia o eliminarlas.  
  
 Puede usar varias herramientas de generación de perfiles en el entorno de desarrollo integrado \(IDE\) para identificar y adaptar estas clases problemas de rendimiento.  Estas herramientas funcionan de la misma manera para los proyectos de SharePoint que para otros tipos de proyectos de Visual Studio.  El Asistente de rendimiento de las Herramientas de generación de perfiles le guía por la creación de una sesión de rendimiento que utiliza las pruebas que especifica.  Una sesión de rendimiento es un conjunto de datos de configuración que se utiliza para obtener información sobre el rendimiento de una aplicación, junto con los resultados de una o más series de perfiles.  Las sesiones de rendimiento se almacenan en su carpeta del proyecto y puede verlas en **Explorador de rendimiento**.  Para obtener más información, vea [Introducción a los métodos de generación de perfiles](../profiling/understanding-performance-collection-methods.md).  
  
 Después de crear y ejecutar un análisis de perfiles en la aplicación, un informe proporciona detalles sobre el rendimiento.  Este informe puede incluir elementos como un gráfico de uso de CPU a lo largo del tiempo, una pila jerárquica de llamada de función o un árbol de llamadas.  El contenido exacto del informe puede variar, dependiendo del tipo de prueba que se ejecuta, como el muestreo o la instrumentación.  Para obtener más información, vea [Información general sobre herramientas de generación de perfiles](http://go.microsoft.com/fwlink/?LinkId=224689).  
  
## Proceso de la sesión de rendimiento  
 Para generar perfiles de una aplicación, comience utilizando el Asistente para rendimiento de las Herramientas de generación de perfiles para crear una sesión de rendimiento.  En la barra de menús, elija **Analizar**, **Iniciar Asistente de rendimiento**.  Cuando se completa el asistente, se escribe la información necesaria para la sesión de rendimiento, como el método de perfil deseado y la aplicación cuyo perfil se desea generar.  Para obtener más información, vea [Cómo: Generar perfiles en un sitio web o una aplicación web mediante el Asistente de rendimiento](http://go.microsoft.com/fwlink/?LinkId=224692).  Como alternativa, puede utilizar opciones de línea de comandos para configurar y ejecutar una sesión de rendimiento.  Para obtener más información, vea [Usar las herramientas de generación de perfiles desde la línea de comandos](http://go.microsoft.com/fwlink/?LinkId=224703).  Si desea configurar cada aspecto de una sesión de rendimiento manualmente, vea [Cómo: Crear manualmente sesiones de rendimiento con las herramientas de generación de perfiles](http://go.microsoft.com/fwlink/?LinkId=224691).  También puede crear una sesión de rendimiento a partir de una prueba unitaria si, en la ventana **Resultados de pruebas**, abre el menú contextual para la prueba unitaria y elige **Crear sesión de rendimiento**.  
  
 Después de configurar una sesión de rendimiento, la configuración de la sesión se guarda, el servidor se configura para proporcionar datos de generación de perfiles y se ejecuta la aplicación.  Cuando se utiliza la aplicación, los datos de rendimiento se escriben en un archivo de registro.  Las sesiones de rendimiento se muestran en **Explorador de rendimiento** en la carpeta **Destinos**.  Una vez finalizada una sesión de rendimiento, el informe aparece en la carpeta **Informes** del **Explorador de rendimiento**.  Para mostrar el informe, ábralo en **Explorador de rendimiento**.  Para ver o configurar las propiedades de una sesión de rendimiento, abra el menú contextual en **Explorador de rendimiento** y elija **Propiedades**.  Para obtener más información sobre propiedades específicas de una sesión de rendimiento, vea [Configurar sesiones de rendimiento para las Herramientas de generación de perfiles](http://go.microsoft.com/fwlink/?LinkId=224694).  Para obtener información sobre cómo interpretar los resultados de una sesión de rendimiento, vea [Analizar los datos de las Herramientas de generación de perfiles](http://go.microsoft.com/fwlink/?LinkId=224704).  
  
## Pruebas de esfuerzo  
 Puede analizar el rendimiento de esfuerzo de las aplicaciones si crea pruebas de carga y pruebas de rendimiento web en Visual Studio Ultimate.  Cuando cree una prueba de carga en Visual Studio, especifique una combinación de factores, denominada escenario, con la que se probará la aplicación.  Estos factores incluyen el patrón de carga, el modelo de combinación de pruebas, la combinación de pruebas, la combinación de redes y la combinación de exploradores web.  Los escenarios de prueba de carga pueden incluir pruebas unitarias y pruebas de rendimiento web.  
  
 Figura 1: Ejemplo de resultados de pruebas de carga  
  
 ![Vista de gráficos de prueba de carga en ejecución](../sharepoint/media/load-webgraphs.png "Vista de gráficos de prueba de carga en ejecución")  
  
 Las pruebas web simulan la posible interacción de un usuario final con una aplicación de SharePoint.  Las pruebas de rendimiento web se pueden crear grabando solicitudes HTTP en una sesión del explorador o mediante la **Grabadora de pruebas de rendimiento web**.  Las solicitudes web aparecen en el **Editor de prueba de rendimiento web** después de que finalice la sesión del explorador.  A continuación, puede depurar los resultados en el **Visor de resultados de pruebas de rendimiento web**.  También puede compilar pruebas de rendimiento web manualmente mediante el **Editor de prueba de rendimiento web**.  
  
## Probar interfaces de usuario  
 Las pruebas de IU codificadas controlan automáticamente la aplicación de SharePoint a través de la interfaz de usuario \(UI\).  Estas pruebas cubren los controles de IU, como botones y menús, para comprobar que funcionan correctamente.  Esta clase de prueba es especialmente útil si la validación u otra lógica se realizan en la interfaz de usuario, por ejemplo, en una página web.  También puede usar las pruebas de IU codificada para automatizar las pruebas manuales.  Las pruebas de IU codificada para las aplicaciones de SharePoint se crean de la misma forma que las pruebas para otros tipos de aplicaciones.  Para obtener más información, vea [Probar aplicaciones de SharePoint 2010 con pruebas de IU codificadas](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md).  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Walkthrough: Profiling a SharePoint Application](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|Muestra cómo realizar un análisis de perfiles de muestreo en una aplicación de SharePoint.|  
|[Create and run a load test](http://msdn.microsoft.com/es-es/7041cbcf-9ab1-4579-98ff-8f296aeaded4)|Describe cómo crear pruebas de carga, que sirven de ayuda para aumentar el esfuerzo de las aplicaciones de SharePoint.|  
|[Creating and Editing Web Performance Tests](http://msdn.microsoft.com/es-es/8bf5f2a7-c693-47d6-9282-5946480151dc)|Describe cómo crear pruebas de rendimiento web, que sirven de ayuda para simular cómo un usuario interactúa con su sitio de SharePoint en la Web.|  
|[Haga una prueba unitaria de su código](../test/unit-test-your-code.md)|Describe cómo buscar errores lógicos en el código mediante pruebas unitarias.|  
|[Probar aplicaciones de SharePoint 2010 con pruebas de IU codificadas](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md)|Describe cómo probar la interfaz de usuario de las aplicaciones de SharePoint.|  
  
## Vea también  
 [Compilar y depurar soluciones de SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Probar la aplicación](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)   
 [Mejorar la calidad del código](../test/improve-code-quality.md)  
  
  