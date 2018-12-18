---
title: 'Cómo: implementar y publicar una solución de SharePoint en un sitio de SharePoint Local | Microsoft Docs'
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
ms.openlocfilehash: e288b5a284ca4155cf70f4458b5b490ca4289cbe
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119810"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Cómo: implementar y publicar una solución de SharePoint en un sitio de SharePoint local
  Puede implementar o publicar soluciones de SharePoint en un servidor de SharePoint local en el equipo de desarrollo. Las copias del proceso de implementación el *.wsp* archivo al servidor de SharePoint, instala la solución y, a continuación, activa las características. La publicación solo copias de procesar el *.wsp* archivo al servidor de SharePoint y lo instala. Debe activar manualmente para habilitarlo en SharePoint.  
  
## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Para implementar una solución de SharePoint en el servidor de SharePoint local  
  
1.  En **el Explorador de soluciones**, elija el proyecto que desea implementar.  
  
2.  En la barra de menús, elija **compilar**, **implementar solución**.  
  
     El *.wsp* archivo se crea y se instala en el servidor de SharePoint local. Además, se activan las características.  
  
## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>Para publicar una solución de SharePoint en un servidor de SharePoint local  
  
1.  En **el Explorador de soluciones**, abra el menú contextual para el proyecto de SharePoint que desea publicar y, a continuación, elija **publicar**.  
  
2.  En el **publicar** diálogo cuadro, elija el **publicar en el sistema de archivos** botón de opción.  
  
3.  En el **ubicación de destino** cuadro de texto, escriba una ruta de acceso local y, a continuación, elija el **publicar** botón.  
  
     Aparece el progreso de la publicación en Visual Studio **salida** ventana. Cuando finalice el proceso, la solución (*.wsp*) está instalado el archivo en el servidor de SharePoint local. Sin embargo, todavía debe activarse para su uso en SharePoint. Si ya existe el archivo de solución, un error se produce y se le pregunta si desea sobrescribir el archivo existente. Para obtener información sobre cómo actualizar el paquete, vea la sección sobre cómo actualizar los paquetes remotos en [Cómo: implementar, publicar y actualizar soluciones de SharePoint en un servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## <a name="see-also"></a>Vea también
 [Cómo: implementar, publicar y actualizar soluciones de SharePoint en un servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [Crear paquetes de solución SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Cómo: personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Cómo: agregar y quitar características y elementos de un paquete mediante el Diseñador de paquetes](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
