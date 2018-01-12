---
title: "Cómo: abrir soluciones de Office sin ejecutar código | Documentos de Microsoft"
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
- Office solutions [Office development in Visual Studio], opening
- opening Office solutions
- bypassing assemblies
- solutions [Office development in Visual Studio], opening
- assemblies [Office development in Visual Studio], bypassing
- Office documents [Office development in Visual Studio, opening without running code
- documents [Office development in Visual Studio], opening without running code
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: bd7a401ab96cbb196d97b2e210b3ede0a624deb8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Cómo: Abrir soluciones de Office sin ejecutar código
  Una solución de Microsoft Office creada con las extensiones de código administrado se ejecuta aunque la configuración de seguridad en la aplicación de Office del usuario final se establece en alta. Esto es porque la seguridad del código de ensamblado .NET está administrado por Microsoft .NET Framework, no por Microsoft Office.  
  
 Sin embargo, hay ocasiones cuando desea abrir un documento sin ejecutar el código. Por ejemplo, código que se ejecuta cuando se abre el documento podría alterar el contenido, pero desea actualizar el aspecto del documento antes de los cambios de código. O desea enviar el documento con cierta información en ella a otra persona, y no desea que el código para ejecutar y posiblemente modificar su contenido.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Hay varias maneras de abrir un documento o un libro que contiene las extensiones de código administrado sin ejecutar el código de ensamblado.  
  
### <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Para omitir el ensamblado usando la tecla MAYÚS  
  
-   Abrir documentos y libros desde el **archivo** menú mientras mantiene presionada la tecla MAYÚS para impedir que generar eventos de inicialización mientras se abre el documento de Word y Excel.  
  
    > [!NOTE]  
    >  Si abre un documento o libro desde el **Introducción** panel de tareas, mantenga presionada la tecla MAYÚS no omite el código. Además, manteniendo presionada la tecla MAYÚS no evita que los eventos que se produzca después de abrir el documento.  
  
     Este método es útil si desea abrir un documento para realizar cambios sin ejecutar el código y modificar primero el documento.  
  
### <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Para omitir un ensamblado con el cambio de nombre o eliminarlo  
  
-   Si tiene los permisos necesarios en el equipo donde se encuentra el ensamblado, puede cambiar el nombre o quite el ensamblado para que el documento o libro no se puede encontrar. Esto genera un error que se produce cada vez que se abre el documento de Office.  
  
     Si la solución es utilizada por varias personas, este método impide que la solución se ejecuta para todas ellas. Esto puede resultar útil si se encuentra un problema en el código o un servidor que se hace referencia y desea evitar que los usuarios lo ejecuten.  
  
## <a name="see-also"></a>Vea también  
 [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Manifiestos de implementación y aplicación en soluciones de Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  