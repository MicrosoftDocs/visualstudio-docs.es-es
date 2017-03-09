---
title: "Crear aplicaciones en lenguajes bidireccionales | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "árabe (idioma), crear aplicaciones"
  - "compatibilidad con idiomas bidireccionales, acerca de la compatibilidad con idiomas bidireccionales"
  - "presentación de caracteres hebreos, crear aplicaciones"
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Crear aplicaciones en lenguajes bidireccionales
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede utilizar Visual Studio para crear aplicaciones que muestren correctamente texto en idiomas escritos de derecha a izquierda, incluidos el árabe y el hebreo.  Para algunas características, sólo puede definir propiedades.  En otros casos, debe implementar las características en el código.  
  
> [!NOTE]
>  Para escribir y mostrar idiomas bidireccionales, debe trabajar con una versión de Windows que esté configurada en el idioma correspondiente.  Puede ser una versión de Windows en inglés con el idioma apropiado instalado; o bien, la versión traducida a ese idioma de Windows.  
  
## Tipos de aplicación que admitan idiomas bidireccionales  
  
1.  Aplicaciones para Windows.  Puede crear aplicaciones totalmente bidireccionales que incluyan compatibilidad con texto bidireccional, orden de lectura de derecha a izquierda y reflejo \(inversión del diseño de las ventanas, los menús, los cuadros de diálogo, etc.\).  Excepto el reflejo, estas características están disponibles de manera predeterminada o como valores de propiedad.  Algunas características, como los cuadros de mensaje, admite el reflejo de manera inherente.  Sin embargo, en otros casos, debe implementar el reflejo en el código.  Para obtener más información, vea [Bi\-Directional Support for Windows Forms Applications](../Topic/Bi-Directional%20Support%20for%20Windows%20Forms%20Applications.md).  
  
2.  Aplicaciones Web.  Los servicios Web y el recibir enviando texto UTF\-8 y Unicode, y adecuadas para aplicaciones que implican idiomas bidireccionales.  Las aplicaciones de cliente web se basan en exploradores para la interfaz de usuario, por lo que el grado de compatibilidad bidireccional en una aplicación web depende de medida el explorador esas características bidireccionales.  En Visual Studio, puede crear aplicaciones que admitan texto árabe y hebreo, el orden de lectura de derecha a izquierda, la codificación de archivos y configuraciones de las referencias culturales locales.  Para obtener más información, vea [Bidirectional Support for ASP.NET Web Applications](../Topic/Bidirectional%20Support%20for%20ASP.NET%20Web%20Applications.md).  
  
3.  Aplicaciones de consola  Las aplicaciones de consola no incluyen compatibilidad de texto con idiomas bidireccionales.  Ésta es una consecuencia de cómo funciona Windows con aplicaciones de consola.  
  
## Características de Visual Studio totalmente compatibles  
 En tiempo de diseño, en Visual Studio, puede utilizar idiomas bidireccionales como se indica a continuación:  
  
-   **Entrada de texto** Visual Studio admite Unicode, de manera que si su sistema está definido con la configuración local y el idioma de entrada apropiados, puede escribir texto en árabe o hebreo. La compatibilidad con el árabe incluye kashida y diacríticos.  
  
-   **Nombres de objeto** Puede utilizar idiomas bidireccionales para asignar nombres a soluciones, proyectos, archivos, carpetas, etc.  En el código, puede utilizar idiomas bidireccionales para los nombres de variables, clases, objetos, atributos, metadatos y otros elementos.  
  
-   **Codificación de archivos** Puede guardar y abrir archivos con una codificación Unicode o específica del idioma.  Para obtener más información, vea [Cómo: Guardar y abrir archivos con codificación](../ide/how-to-save-and-open-files-with-encoding.md).  
  
## Características con compatibilidad limitada o no compatibles  
 Otras características comunes a las aplicaciones en idiomas bidireccionales no son totalmente compatibles con Visual Studio o, en algunos caso, no lo son en absoluto.  Incluyen los siguientes:  
  
-   **Orden de lectura de derecha a izquierda** De manera predeterminada, los controles de entrada de texto que se utilizan en Visual Studio usan el orden de lectura de izquierda a derecha.  En la mayoría de los casos, puede utilizar gestos estándar de Windows para cambiar el orden de lectura.  Por ejemplo, puede presionar Ctrl\+Mayús derecha para cambiar la ventana Propiedades para que admita el orden de lectura de derecha a izquierda para valores de propiedad.  
  
     Sin embargo, el orden de lectura de derecha a izquierda no se admite en todas las partes de Visual Studio.  Excepciones:  
  
    -   Las casillas, las listas desplegables y otros controles de los cuadros de diálogo de Visual Studio utilizan siempre el orden de lectura de izquierda a derecha.  
  
    -   El Editor de código \(y el Editor de texto\) no admite el orden de lectura de derecha a izquierda.  Puede escribir texto en un idioma bidireccional, pero el orden de lectura será siempre de izquierda a derecha.  
  
## Dar nombre a las cosas mediante texto en árabe o hebreo  
 Puede utilizar texto árabe o hebreo para asignar nombres a carpetas, variables u otros objetos.  Cuando trabaje con el árabe, puede utilizar cualesquiera caracteres árabes, incluidos kashida y diacríticos.  
  
 A los siguientes elementos se les puede dar nombre utilizando el árabe o el hebreo y Visual Studio los controlará correctamente:  
  
-   Nombres de solución, proyecto y archivo, entre ellas las carpetas que incluya en la ruta de acceso del proyecto.  El Explorador de soluciones mostrará correctamente los nombres de solución y elemento.  
  
-   Contenido de los archivos.  Puede abrir o guardar archivos con codificación Unicode o con una página de códigos seleccionada.  
  
    > [!NOTE]
    >  El editor de código es un caso especial.  Más adelante se incluye información detallada.  
  
-   Elementos de datos.  El **Explorador de servidores** mostrará estos elementos correctamente y permitirá editarlos.  
  
-   Elementos copiados en el Portapapeles de Windows.  
  
-   Atributos y metadatos.  
  
-   Valores de propiedad.  Puede utilizar texto árabe o hebreo en la ventana Propiedades.  La ventana permite cambiar entre el orden de lectura de derecha a izquierda y viceversa, utilizando combinaciones de teclas estándar de Windows \(Ctrl\+Mayús derecha para el orden de derecha a izquierda, y Ctrl\+Mayús izquierda para el orden de izquierda a derecha\).  
  
-   Código y texto literal.  En el Editor de código \(que es también el Editor de texto\), puede utilizar el árabe o el hebreo para dar nombre a clases, funciones, variables, propiedades, literales de cadena, atributos, etc.  Sin embargo, el editor no admite el orden de lectura de derecha a izquierda; el texto siempre comienza en el margen izquierdo.  
  
    > [!TIP]
    >  Se recomienda colocar los literales de cadena en archivos de recursos en lugar de codificarlos en los programas.  Para obtener más información, vea [Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5).  
  
    > [!NOTE]
    >  Debe ser coherente a la hora de hacer referencia a objetos denominados con estos idiomas.  Por ejemplo, si utiliza kashida para dar nombre a una variable árabe, debe utilizar siempre kashida cuando haga referencia a esa variable; de lo contrario, se producirán errores.  
  
-   Comentarios de código.  Puede crear comentarios en árabe o hebreo.  También puede utilizar estos idiomas en el generador de comentarios.  
  
## Vea también  
 [Bi\-Directional Support for Windows Forms Applications](../Topic/Bi-Directional%20Support%20for%20Windows%20Forms%20Applications.md)   
 [Bidirectional Support for ASP.NET Web Applications](../Topic/Bidirectional%20Support%20for%20ASP.NET%20Web%20Applications.md)   
 [Globalizar aplicaciones](../ide/globalizing-applications.md)   
 [Localizar aplicaciones](../ide/localizing-applications.md)