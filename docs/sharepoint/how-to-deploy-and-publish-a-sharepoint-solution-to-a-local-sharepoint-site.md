---
title: Implementar & publicar una solución de SharePoint en el sitio de SharePoint local
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 78a837cc7145187fbc529e6e86cc27f88dd81f51
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585802"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Cómo: implementar y publicar una solución de SharePoint en un sitio de SharePoint local
  Puede implementar o publicar soluciones de SharePoint en un servidor de SharePoint local en el equipo de desarrollo. El proceso de implementación copia el archivo *. wsp* en el servidor de SharePoint, instala la solución y, a continuación, activa las características. El proceso de publicación solo copia el archivo *. wsp* en el servidor de SharePoint y lo instala. Debe activarla manualmente para habilitarla en SharePoint.

## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Para implementar una solución de SharePoint en el servidor de SharePoint local

1. En **Explorador de soluciones**, elija el proyecto que desea implementar.

2. En la barra de menús, elija **compilar**, **implementar solución**.

     El archivo *. wsp* se crea y se instala en el servidor local de SharePoint. Además, las características se activan.

## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>Para publicar una solución de SharePoint en un servidor de SharePoint local

1. En **Explorador de soluciones**, abra el menú contextual del proyecto de SharePoint que desea publicar y, a continuación, elija **publicar**.

2. En el cuadro de diálogo **publicar** , elija el botón de opción **publicar en sistema de archivos** .

3. En el cuadro de texto **Ubicación de destino** , escriba una ruta de acceso local y, a continuación, elija el botón **publicar** .

     El progreso de la publicación aparece en la ventana **resultados** de Visual Studio. Una vez finalizado el proceso, el archivo de solución (*. wsp*) se instala en el servidor local de SharePoint. Sin embargo, todavía se debe activar para su uso en SharePoint. Si el archivo de solución ya existe, se produce un error que le pregunta si desea sobrescribir el archivo existente. Para obtener información sobre cómo actualizar el paquete, vea la sección sobre cómo actualizar paquetes remotos en [Cómo: implementar, publicar y actualizar soluciones de SharePoint en un servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Vea también
- [Cómo: implementar, publicar y actualizar soluciones de SharePoint en un servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)
- [Crear paquetes de soluciones de SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Cómo: personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Cómo: agregar y quitar características y elementos de un paquete mediante el diseñador de paquetes](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
