---
title: "Soluciones de VBA y Office en Visual Studio en comparación con | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
ms.assetid: 31756c2f-8829-4011-ad77-134cb3728344
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1b83d4d9064132be9a8b007dd46c9c360f5fed1e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>Comparación de soluciones de VBA y Office en Visual Studio
  Microsoft Visual Basic para aplicaciones (VBA) utiliza código no administrado que se integra estrechamente con las aplicaciones de Office. Los proyectos de Microsoft Office creados con Visual Studio le permiten sacar partido de .NET Framework y las herramientas de diseño de Visual Studio.  
  
 Para obtener información acerca de los tipos de soluciones de Office que puede crear mediante Visual Studio, vea [información general sobre el desarrollo de soluciones de Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="comparison"></a>Comparación  
 En la tabla siguiente se proporciona una comparación básica entre las soluciones de VBA y de Office en Visual Studio.  
  
|Soluciones de VBA|Soluciones de Office en Visual Studio|  
|-------------------|---------------------------------------|  
|Utiliza código que está conectado a un documento concreto y se conserva en él.|Usa el código que se almacena de manera independiente con respecto al documento (para personalizaciones de nivel de documento), o en un ensamblado que carga la aplicación (para complementos VSTO).|  
|Funciona con los modelos de objetos de Office y las API de VBA.|Proporciona acceso a los modelos de objetos de Office y a las API de [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .|  
|Diseñado para la grabación de macros y para proporcionar una experiencia de desarrollo más sencilla.|Diseñado para proporcionar seguridad, facilitar el mantenimiento del código y permitir utilizar todo el entorno de desarrollo integrado (IDE) de Visual Studio.|  
|Funciona bien con soluciones que se benefician de una integración muy estrecha con las aplicaciones de Office.|Funciona bien con soluciones que se benefician de todos los recursos de Visual Studio y [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].|  
|Tiene limitaciones para las empresas, especialmente en las áreas de seguridad e implementación.|Se ha diseñado para su uso en empresas.|  
  
 Algunas cosas siguen siendo más fáciles de hacer rápidamente con VBA. En concreto, se recomienda seguir utilizando VBA para:  
  
-   Funciones de hoja de cálculo personalizadas.  
  
-   Grabación de macros.  
  
## <a name="combining-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>Combinar soluciones de VBA y soluciones de Office creadas con Visual Studio  
 Puede llamar a código de VBA desde soluciones de Office creadas con Visual Studio. Asimismo, puede llamar a código en soluciones de Office creadas con Visual Studio desde VBA. La técnica específica será diferente dependiendo de si la solución de Office es un complemento VSTO o una personalización de nivel de documento. Para obtener más información, vea [Calling Code in VSTO Add-ins from Other Office Solutions](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) y [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre el desarrollo de soluciones de Office &#40; VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Llamar a código en complementos VSTO desde otras soluciones de Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md)   
 [Arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md)   
 [Arquitectura de complementos VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md)   
 [Introducción a &#40; desarrollo de Office en Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
  
  