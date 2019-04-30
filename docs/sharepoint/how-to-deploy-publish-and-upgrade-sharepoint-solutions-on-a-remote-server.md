---
title: Procedimiento Implementar, publicar y actualizar soluciones de SharePoint en un servidor remoto | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- remote deployment [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, remote deployment
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fdaebbc8901330236769331453501bebdd3f98a3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62813948"
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>Procedimiento Implementar, publicar y actualizar soluciones de SharePoint en un servidor remoto
  Además de implementar las soluciones de SharePoint en el sistema local, puede publicar soluciones en espacio aislado de SharePoint para sitios de SharePoint locales o sitios remotos. Las copias de proceso de publicación remota la *.wsp* archivo en el servidor de SharePoint instala la solución y, a continuación, le permite activar la solución. También puede actualizar una instalación remota de solución de SharePoint después de realizar cambios en él.

## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>Para publicar una solución en espacio aislado de SharePoint en un servidor remoto de SharePoint

1. En **el Explorador de soluciones**, abra el menú contextual para el proyecto de SharePoint en espacio aislado que desea publicar y, a continuación, elija **publicar**.

2. En el **publicar** diálogo cuadro, elija el **publicar en el sitio de SharePoint** botón de opción y, a continuación, escriba una dirección URL para un sitio de publicación en línea, como: `https://mytestsite.sharepoint.microsoftonline.com`.

3. Elija la **abrir la página de la Galería de soluciones en el explorador después de la publicación** botón de opción para ver la lista de soluciones en la **Galería de soluciones** página después de la publicación.

4. Elija la **publicar** botón.

5. Inicie sesión en el servidor remoto si se requiere autenticación de usuario.

     Aparece el progreso de la publicación en Visual Studio **salida** ventana. Cuando finalice el proceso, la solución (*.wsp*) está instalado el archivo en el servidor de SharePoint remoto. Sin embargo, todavía debe activarse antes de que se puede usar en SharePoint.

6. En el **Galería de soluciones** , seleccione la aplicación de SharePoint y, a continuación, en la cinta de opciones, elija la **activar** botón.

7. En el **activar solución** cuadro de diálogo, en la cinta de opciones, elija la **activar** nuevamente en el botón.

     El **estado** columna en el **Galería de soluciones** página indica que la aplicación está activa.

## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>Para actualizar una solución en espacio aislado de SharePoint en un servidor remoto de SharePoint
 Si una solución en espacio aislado de SharePoint ya está publicada en un servidor remoto, el siguiente proceso le permite actualizarlo después de realizar cambios a la aplicación en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

1. El nombre del paquete de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para ello, en **el Explorador de soluciones** abrir el paquete. Aparece en el **Explorador de paquetes**.

2. En **Explorador de paquetes**, en el **nombre** , cambie el nombre del paquete a un nombre único.

3. Guarde el proyecto.

4. En **el Explorador de soluciones**, abra el menú contextual para el proyecto y, a continuación, elija **publicar**.

5. En el **publicar** diálogo cuadro, elija el **publicar en el sitio de SharePoint** botón de opción y, a continuación, si falta la dirección URL para el servidor remoto donde se guarda la solución, escriba lo.

6. Elija la **abrir la página de la Galería de soluciones en el explorador después de la publicación** botón de opción para ver la lista de soluciones en la **Galería de soluciones** página después de la publicación.

7. Elija la **publicar** botón.

8. Inicie sesión en el servidor remoto si se requiere autenticación de usuario.

     Si ha iniciado sesión el servidor remoto recientemente, la autenticación no es posible que sea necesaria.

     Si todavía existe la versión anterior de la aplicación que tiene el mismo nombre en el servidor de SharePoint, obtendrá un error que un paquete con el mismo nombre ya existe en el servidor de SharePoint. Debe cambiar el nombre del paquete a un nombre único antes de la publicación.

9. Elija la nueva aplicación en SharePoint y, a continuación, en la cinta de opciones, elija la **actualizar** botón.

10. En el **Actualizar solución** cuadro de diálogo, en la cinta de opciones, elija la **actualizar** nuevamente en el botón. El **estado** columna en el **Galería de soluciones** página ahora debe indicar que la aplicación está activa.

     La versión anterior de la solución está desactivada, la nueva versión de la solución se actualiza con los datos mantenidos en la solución antigua y se activa la nueva solución en SharePoint.

## <a name="see-also"></a>Vea también
- [Cómo: Implementar y publicar una solución de SharePoint en un sitio de SharePoint local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)
- [Crear paquetes de solución SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Cómo: Personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Cómo: Agregar y quitar características y elementos de un paquete mediante el Diseñador de paquetes](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
