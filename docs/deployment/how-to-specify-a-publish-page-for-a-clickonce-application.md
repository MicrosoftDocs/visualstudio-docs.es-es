---
title: Cómo especificar una página de publicación para una aplicación ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: acf7178a6b5456d048421533b8497682d69c2ee0
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2020
ms.locfileid: "85381969"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Cómo: Especificar una página de publicación para una aplicación ClickOnce
Al publicar una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación, se genera una página web predeterminada (publish.htm) y se publica junto con la aplicación. Esta página contiene el nombre de la aplicación, un vínculo para instalar la aplicación y/o los requisitos previos, y un vínculo a un tema de ayuda que describe [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . La propiedad **publicar página** del proyecto le permite especificar un nombre para la Página Web de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación.

 Una vez especificada la página de publicación, la próxima vez que publique, se copiará en la ubicación de publicación. no se sobrescribirá si vuelve a publicar. Si desea personalizar la apariencia de la página, puede hacerlo sin preocuparse por perder los cambios. Para obtener más información, vea [Cómo: personalizar la página web predeterminada de ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).

 La propiedad **publicar página** se puede establecer en el cuadro de diálogo **Opciones de publicación** , accesible desde el panel **publicar** del diseñador de **proyectos**.

### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Para especificar una página web personalizada para una aplicación ClickOnce

1. Con un proyecto seleccionado en **Explorador de soluciones**, en el menú **proyecto** , haga clic en **propiedades**.

2. Seleccione el panel **publicar** .

3. Haga clic en el botón **Opciones** para abrir el cuadro de diálogo **Opciones de publicación** .

4. Haga clic en **Implementación**.

5. En el cuadro de diálogo **Opciones de publicación** , asegúrese de que la casilla **abrir la Página Web de implementación después** de la publicación esté activada (debe estar seleccionada de forma predeterminada).

6. En el cuadro **Página Web de implementación** , escriba el nombre de la página web y, a continuación, haga clic en **Aceptar**.

### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Para evitar que se inicie la página de publicación cada vez que publique

1. Con un proyecto seleccionado en **Explorador de soluciones**, en el menú **proyecto** , haga clic en **propiedades**.

2. Seleccione el panel **publicar** .

3. Haga clic en el botón **Opciones** para abrir el cuadro de diálogo **Opciones de publicación** .

4. Haga clic en **Implementación**.

5. En el cuadro de diálogo **Opciones de publicación** , desactive la casilla **abrir la Página Web de implementación después de publicar** .

## <a name="see-also"></a>Consulte también
- [Publicación de aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Cómo: Personalizar la página web predeterminada para ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)