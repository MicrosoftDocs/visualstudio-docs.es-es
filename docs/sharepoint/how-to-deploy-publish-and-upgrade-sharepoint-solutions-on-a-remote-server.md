---
title: Implementar, publicar, & actualizar soluciones de SharePoint de forma remota
titleSuffix: ''
description: Implementar, publicar y actualizar soluciones de SharePoint en espacio aislado en un sitio remoto o en un sitio de SharePoint local.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: db476af4a9d3be9cab2109fb3489d0767765075f
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903577"
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>Cómo: implementar, publicar y actualizar soluciones de SharePoint en un servidor remoto
  Además de implementar soluciones de SharePoint en el sistema local, puede publicar soluciones de SharePoint en espacio aislado en sitios remotos o sitios locales de SharePoint. El proceso de publicación remota copia el archivo *. wsp* en el servidor de SharePoint, instala la solución y, a continuación, le permite activar la solución. También puede actualizar una instalación de una solución de SharePoint remota después de que se realicen cambios en ella.

## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>Para publicar una solución de SharePoint en espacio aislado en un servidor de SharePoint remoto

1. En **Explorador de soluciones**, abra el menú contextual del proyecto de SharePoint en espacio aislado que desea publicar y, a continuación, elija **publicar**.

2. En el cuadro de diálogo **publicar** , elija el botón de opción **publicar en el sitio de SharePoint** y, a continuación, escriba una dirección URL para un sitio de publicación en línea, como: `https://mytestsite.sharepoint.microsoftonline.com` .

3. Elija la **Página abrir la galería de soluciones en el** botón de opción explorador después de la publicación para ver la lista de soluciones en la página de la **Galería de soluciones** después de la publicación.

4. Elija el botón **Publicar**.

5. Inicie sesión en el servidor remoto si se requiere la autenticación del usuario.

     El progreso de la publicación aparece en la ventana **resultados** de Visual Studio. Una vez finalizado el proceso, el archivo de solución (*. wsp*) se instala en el servidor remoto de SharePoint. Sin embargo, todavía se debe activar antes de que se pueda usar en SharePoint.

6. En la página **Galería de soluciones** , seleccione la aplicación de SharePoint y, a continuación, en la cinta de opciones, elija el botón **Activar** .

7. En el cuadro de diálogo **Activar solución** , en la cinta de opciones, vuelva a elegir el botón **Activar** .

     La columna **Estado** de la página de la **Galería de soluciones** indica que la aplicación está activa.

## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>Para actualizar una solución de SharePoint en espacio aislado en un servidor de SharePoint remoto
 Si una solución de SharePoint en espacio aislado ya está publicada en un servidor remoto, el siguiente proceso le permite actualizarla después de realizar cambios en la aplicación en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

1. Cambie el nombre del paquete de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Para ello, en **Explorador de soluciones** Abra el paquete. Aparece en el **Explorador de paquetes**.

2. En el **Explorador de paquetes**, en el cuadro **nombre** , cambie el nombre del paquete por un nombre único.

3. Guarde el proyecto.

4. En **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **publicar**.

5. En el cuadro de diálogo **publicar** , elija el botón de opción **publicar en el sitio de SharePoint** y, a continuación, si falta la dirección URL del servidor remoto en el que se guarda la solución, escríbala.

6. Elija la **Página abrir la galería de soluciones en el** botón de opción explorador después de la publicación para ver la lista de soluciones en la página de la **Galería de soluciones** después de la publicación.

7. Elija el botón **Publicar**.

8. Inicie sesión en el servidor remoto si se requiere la autenticación del usuario.

     Si ha iniciado sesión en el servidor remoto recientemente, es posible que no sea necesaria la autenticación.

     Si la versión anterior de la aplicación que tiene el mismo nombre sigue existiendo en el servidor de SharePoint, obtendrá un error que le proporcionará que ya existe un paquete con el mismo nombre en el servidor de SharePoint. Debe cambiar el nombre del paquete por un nombre único antes de la publicación.

9. Elija la nueva aplicación en SharePoint y, a continuación, en la cinta de opciones, elija el botón **Actualizar** .

10. En el cuadro de diálogo **Actualizar solución** , en la cinta de opciones, vuelva a elegir el botón **Actualizar** . En la columna **Estado** de la página de la **Galería de soluciones** ahora debe indicar que la aplicación está activa.

     La versión anterior de la solución está desactivada, la nueva versión de la solución se actualiza con los datos que se mantienen de la solución anterior y la nueva solución se activa en SharePoint.

## <a name="see-also"></a>Consulte también
- [Cómo: implementar y publicar una solución de SharePoint en un sitio de SharePoint local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)
- [Crear paquetes de soluciones de SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Cómo: personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Cómo: agregar y quitar características y elementos de un paquete mediante el diseñador de paquetes](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
