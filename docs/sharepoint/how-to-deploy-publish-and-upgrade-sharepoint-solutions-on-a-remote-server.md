---
title: "Cómo: implementar, publicar y actualizar soluciones de SharePoint en un servidor remoto | Documentos de Microsoft"
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
- remote deployment [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, remote deployment
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
ms.assetid: d9c67fae-d097-4e26-a2b9-0f72ff800987
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 115509e8ff79aafa703c429b476041d558e3167c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>Cómo: Implementar, publicar y actualizar una solución de SharePoint en un servidor remoto
  Además de implementar soluciones de SharePoint en el sistema local, puede publicar soluciones de SharePoint en espacio aislado en sitios remotos o sitios locales de SharePoint. El proceso de publicación remoto copia el archivo .wsp en el servidor de SharePoint, instala la solución y, a continuación, le permite activar la solución. También puede actualizar una instalación remota de solución de SharePoint después de realizar cambios en él.  
  
## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>Para publicar una solución en espacio aislado de SharePoint en un servidor remoto de SharePoint  
  
1.  En **el Explorador de soluciones**, abra el menú contextual para el proyecto de SharePoint en espacio aislado que desea publicar y, a continuación, elija **publicar**.  
  
2.  En el **publicar** diálogo cuadro, elija la **publicar en un sitio de SharePoint** botón de opción y, a continuación, escriba una dirección URL para un sitio de publicación en línea, como en el ejemplo siguiente: **https:// mytestsite.SharePoint.microsoftonline.com**.  
  
3.  Elija la **abrir la página de la Galería de soluciones en el explorador después de publicarlo** botón de opción para ver la lista de soluciones en el **Galería de soluciones** página después de la publicación.  
  
4.  Elija la **publicar** botón.  
  
5.  Inicie sesión en el servidor remoto si se requiere autenticación de usuario.  
  
     El progreso de la publicación aparece en Visual Studio **salida** ventana. Cuando finalice el proceso, el archivo de solución (.wsp) se instala en el servidor remoto de SharePoint. Sin embargo, todavía debe activarse antes de que se puede usar en SharePoint.  
  
6.  En el **Galería de soluciones** , seleccione la aplicación de SharePoint y, a continuación, en la cinta de opciones, elija la **activar** botón.  
  
7.  En el **activar solución** cuadro de diálogo, en la cinta de opciones, elija la **activar** nuevamente en el botón.  
  
     El **estado** columna en el **Galería de soluciones** página indica que la aplicación esté activa.  
  
## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>Para actualizar una solución en espacio aislado de SharePoint en un servidor remoto de SharePoint  
 Si una solución en espacio aislado de SharePoint ya está publicada en un servidor remoto, el siguiente proceso le permite actualizarlo después de realizar cambios en la aplicación en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
1.  El nombre del paquete de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para ello, en **el Explorador de soluciones** abrir el paquete. Aparece en el **Explorador de paquetes**.  
  
2.  En **Explorador de paquetes**, en la **nombre** , cambie el nombre del paquete en un nombre único.  
  
3.  Guarde el proyecto.  
  
4.  En **el Explorador de soluciones**, abra el menú contextual para el proyecto y, a continuación, elija **publicar**.  
  
5.  En el **publicar** diálogo cuadro, elija la **publicar en un sitio de SharePoint** botón de opción y, a continuación, si falta la dirección URL para el servidor remoto donde se guarda la solución, escríbelo a.  
  
6.  Elija la **abrir la página de la Galería de soluciones en el explorador después de publicarlo** botón de opción para ver la lista de soluciones en el **Galería de soluciones** página después de la publicación.  
  
7.  Elija la **publicar** botón.  
  
8.  Inicie sesión en el servidor remoto si se requiere autenticación de usuario.  
  
     Si ha iniciado sesión el servidor remoto recientemente, puede que la autenticación no sean necesaria.  
  
     Si todavía existe la versión anterior de la aplicación que tiene el mismo nombre en el servidor de SharePoint, obtendrá un error que un paquete con el mismo nombre ya existe en el servidor de SharePoint. Debe cambiar el nombre del paquete en un nombre único antes de la publicación.  
  
9. Elija la nueva aplicación de SharePoint y, a continuación, en la cinta de opciones, elija la **actualizar** botón.  
  
10. En el **Actualizar solución** cuadro de diálogo, en la cinta de opciones, elija la **actualizar** nuevamente en el botón. El **estado** columna en el **Galería de soluciones** página ahora debe indicar que la aplicación esté activa.  
  
     La versión anterior de la solución está desactivada, la nueva versión de la solución se actualiza con los datos que se mantienen de la solución anterior y se activa la nueva solución en SharePoint.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: implementar y publicar una solución de SharePoint en un sitio de SharePoint Local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)   
 [Crear paquetes de soluciones de SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Cómo: personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Cómo: Agregar y quitar características y elementos de un paquete con el Diseñador de paquetes](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  