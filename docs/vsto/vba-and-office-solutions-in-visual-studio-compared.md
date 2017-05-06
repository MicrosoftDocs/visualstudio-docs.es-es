---
title: "Comparaci&#243;n de soluciones de VBA y Office en Visual Studio"
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
  - "Código VBA, extensiones de código administrado"
  - "extensiones de código administrado [desarrollo de Office en Visual Studio], VBA en comparación con"
ms.assetid: 31756c2f-8829-4011-ad77-134cb3728344
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Comparaci&#243;n de soluciones de VBA y Office en Visual Studio
  Microsoft Visual Basic para aplicaciones \(VBA\) utiliza código no administrado que se integra estrechamente con las aplicaciones de Office. Los proyectos de Microsoft Office creados con Visual Studio le permiten sacar partido de .NET Framework y las herramientas de diseño de Visual Studio.  
  
 Para obtener información acerca de los tipos de soluciones de Office que puede crear con Visual Studio, consulte [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
## Comparación  
 En la tabla siguiente se proporciona una comparación básica entre las soluciones de VBA y de Office en Visual Studio.  
  
|Soluciones de VBA|Soluciones de Office en Visual Studio|  
|-----------------------|-------------------------------------------|  
|Utiliza código que está conectado a un documento concreto y se conserva en él.|Usa el código que se almacena de manera independiente con respecto al documento \(para personalizaciones de nivel de documento\), o en un ensamblado que carga la aplicación \(para complementos VSTO\).|  
|Funciona con los modelos de objetos de Office y las API de VBA.|Proporciona acceso a los modelos de objetos de Office y a las API de [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].|  
|Diseñado para la grabación de macros y para proporcionar una experiencia de desarrollo más sencilla.|Diseñado para proporcionar seguridad, facilitar el mantenimiento del código y permitir utilizar todo el entorno de desarrollo integrado \(IDE\) de Visual Studio.|  
|Funciona bien con soluciones que se benefician de una integración muy estrecha con las aplicaciones de Office.|Funciona bien con soluciones que se benefician de todos los recursos de Visual Studio y [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].|  
|Tiene limitaciones para las empresas, especialmente en las áreas de seguridad e implementación.|Se ha diseñado para su uso en empresas.|  
  
 Algunas cosas siguen siendo más fáciles de hacer rápidamente con VBA. En concreto, se recomienda seguir utilizando VBA para:  
  
-   Funciones de hoja de cálculo personalizadas.  
  
-   Grabación de macros.  
  
## Combinar soluciones de VBA y soluciones de Office creadas con Visual Studio  
 Puede llamar a código de VBA desde soluciones de Office creadas con Visual Studio. Asimismo, puede llamar a código en soluciones de Office creadas con Visual Studio desde VBA. La técnica específica será diferente dependiendo de si la solución de Office es un complemento VSTO o una personalización de nivel de documento. Para obtener más información, vea [Llamar a código en complementos de VSTO desde otras soluciones de Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) y [Combinar personalizaciones de VBA y de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
## Vea también  
 [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Llamar a código en complementos de VSTO desde otras soluciones de Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Combinar personalizaciones de VBA y de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md)   
 [Arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md)   
 [Arquitectura de complementos de VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md)   
 [Introducción &#40;Desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
  
  