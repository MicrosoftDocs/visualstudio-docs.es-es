---
title: Procedimiento Personalizar la página Web predeterminada para una aplicación ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish.htm Web page
- ClickOnce deployment default Web page
- deploying applications [ClickOnce], publishing
- publishing, ClickOnce
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 324066d1f6bd6ad1719b2dc960de2b2357ec8cbd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976386"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Procedimiento Personalización de la página web predeterminada para una aplicación ClickOnce
Al publicar una aplicación ClickOnce en la Web, una página Web generada automáticamente y publicada junto con la aplicación. La página predeterminada contiene el nombre de la aplicación y los vínculos para instalar la aplicación, instale los requisitos previos o acceder a la Ayuda en MSDN.  
  
> [!NOTE]
>  Los vínculos que aparecen en la página dependen del equipo donde se está visualizando la página y qué requisitos previos que se va a incluir.  
  
 El nombre predeterminado para la página Web es *Publish.htm*; puede cambiar el nombre de la **Diseñador de proyectos**. Para obtener más información, vea [Cómo: Especificación de una página de publicación para una aplicación ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).  
  
 El *Publish.htm* se publica la página Web sólo si se detecta una versión más reciente.  
  
> [!NOTE]
>  Los cambios que realice en su **publicar** configuración no afectará la *Publish.htm* página, con una excepción: si agrega o quita los requisitos previos después de publicar inicialmente, volverá a la lista de requisitos previos ya no será exacto. Deberá editar el texto del vínculo de requisitos previos reflejar los cambios.  
  
### <a name="to-customize-the-publish-web-page"></a>Para personalizar la página Web de publicación  
  
1.  Publicar la aplicación ClickOnce para una ubicación Web. Para obtener más información, vea [Cómo: Publicación de una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
2.  En el servidor Web, abra el *Publish.htm* archivo en el Diseñador Web Visual u otro editor de HTML.  
  
3.  Personalizar la página según sea necesario y guárdelo.  
  
4.  Opcional. Para evitar que Visual Studio sobrescriba la página Web de publicación personalizada, desactive la opción **generar automáticamente la página Web de implementación después de cada publicación** en el **opciones de publicación** cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Requisitos previos de instalación con una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Cómo: Especificación de una página de publicación para una aplicación ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)