---
title: "Implementar una solución de Office | Documentos de Microsoft"
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
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office applications [Office development in Visual Studio], deploying Office solutions
- Office development in Visual Studio, deploying Office solutions
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- deploying applications [Office development in Visual Studio], Office solutions (2007 system)
- Office development in Visual Studio, troubleshooting
- Office development in Visual Studio, event viewer
- ClickOnce deployment [Office development in Visual Studio], about ClickOnce solution deployments
- Office solutions [Office development in Visual Studio], deploying
- deploying applications [Office development in Visual Studio], troubleshooting
- solutions [Office development in Visual Studio], deploying Office solutions (2007 system)
ms.assetid: 4cdf4bc6-72c5-4166-8019-d5fd61281079
caps.latest.revision: "78"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8c22db51700a711bed0edd2d5a8431d6dc64c281
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-an-office-solution"></a>Implementar una solución de Office
  Puede implementar soluciones de Office mediante ClickOnce o Windows Installer. Si usa ClickOnce, se reducirá el número de pasos que requiere la implementación y actualización de la solución. Si utiliza Windows Installer, obtendrá control sobre cómo se instala la solución y qué páginas muestra el programa de instalación cuando los usuarios instalan la solución.  
  
> [!NOTE]  
>  ¿Está interesado en el desarrollo de soluciones que amplían la experiencia de Office en [varias plataformas](https://dev.office.com/add-in-availability)? Visite la nueva [modelo de complementos de Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Complementos de Office tienen una superficie pequeña en comparación con las soluciones y complementos VSTO, y puede compilarlas mediante prácticamente cualquier tecnología, como HTML5, JavaScript, CSS3 y XML de programación web.  
  
## <a name="deploying-a-solution-by-using-clickonce"></a>Implementar una solución mediante ClickOnce  
 Al implementar una solución mediante ClickOnce, esta se publica en una ubicación centralizada donde los usuarios pueden instalarla y ejecutarla. Puede actualizar la solución sin tener que distribuir un nuevo programa de instalación a los usuarios.  Esta opción de implementación es más sencilla, pero no puede mostrar a los usuarios las páginas de instalación personalizadas. Además, las soluciones se deben instalar varias veces en cualquier equipo que tenga más de un usuario. Vea [implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="deploying-a-solution-by-using-windows-installer"></a>Implementar una solución mediante Windows Installer  
 Al implementar una solución mediante Windows Installer, distribuirá un programa de instalación a los usuarios y los usuarios instalarán la solución mediante ese programa. El programa de instalación puede instalar una solución para todos los usuarios de un equipo a la vez, en lugar de solo para el usuario actual. También tendrá un poco más de control sobre las opciones que se muestran a los usuarios cuando instalan la solución. Por ejemplo, puede mostrar un contrato de licencia o permitir que los usuarios instalen componentes específicos de una solución. Sin embargo, si actualiza la solución, debe distribuir un nuevo programa de instalación. Vea [implementar una solución de Office mediante Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
## <a name="see-also"></a>Vea también  
 [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md)   
 [Implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Implementar una solución de Office mediante Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md)   
 [Solución de problemas de implementación de las soluciones de Office](../vsto/troubleshooting-office-solution-deployment.md)  
  
  