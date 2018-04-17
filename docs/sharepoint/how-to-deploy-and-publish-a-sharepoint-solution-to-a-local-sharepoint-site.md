---
title: 'Cómo: implementar y publicar una solución de SharePoint en un sitio de SharePoint Local | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5c4f7e347f9cea3a73ab5326b42720a1b2c33529
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Cómo: Implementar y publicar una solución de SharePoint en un sitio de SharePoint local
  Puede implementar o publicar soluciones de SharePoint en un servidor de SharePoint local en el equipo de desarrollo. El proceso de implementación copia el archivo .wsp en el servidor de SharePoint, instala la solución y, a continuación, activa las características. El proceso de publicación solo copia el archivo .wsp en el servidor de SharePoint y lo instala. Debe activar manualmente para habilitar en SharePoint.  
  
## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Para implementar una solución de SharePoint en el servidor de SharePoint local  
  
1.  En **el Explorador de soluciones**, elija el proyecto que desea implementar.  
  
2.  En la barra de menús, elija **generar**, **implementar solución**.  
  
     El archivo .wsp se crea y se instala en el servidor de SharePoint local. Además, se activan las características.  
  
## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>Para publicar una solución de SharePoint en un servidor de SharePoint local  
  
1.  En **el Explorador de soluciones**, abra el menú contextual para el proyecto de SharePoint que desea publicar y, a continuación, elija **publicar**.  
  
2.  En el **publicar** diálogo cuadro, elija la **publicar en el sistema de archivos** botón de opción.  
  
3.  En el **ubicación de destino** cuadro de texto, escriba una ruta de acceso local y, a continuación, elija la **publicar** botón.  
  
     El progreso de la publicación aparece en Visual Studio **salida** ventana. Cuando finalice el proceso, el archivo de solución (.wsp) se instala en el servidor de SharePoint local. Sin embargo, todavía debe activarse para su uso en SharePoint. Si ya existe el archivo de solución, un error se produce y se le pregunta si desea sobrescribir el archivo existente. Para obtener información sobre cómo actualizar el paquete, vea la sección sobre cómo actualizar paquetes remotos en [Cómo: implementar, publicar y actualizar soluciones de SharePoint en un servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: implementar, publicar y actualizar soluciones de SharePoint en un servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [Crear paquetes de soluciones de SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Cómo: personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Cómo: Agregar y quitar características y elementos de un paquete con el Diseñador de paquetes](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  