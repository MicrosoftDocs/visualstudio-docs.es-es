---
title: 'Cómo: personalizar la página Web predeterminada para una aplicación ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: b87019a824acada616865fd65cfd6aade8aa6ec9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49243430"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Cómo: Personalizar la página web predeterminada para una aplicación ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al publicar una aplicación ClickOnce en la Web, una página Web generada automáticamente y publicada junto con la aplicación. La página predeterminada contiene el nombre de la aplicación y los vínculos para instalar la aplicación, instale los requisitos previos o acceder a la Ayuda en MSDN.  
  
> [!NOTE]
>  Los vínculos que aparecen en la página dependen del equipo donde se está visualizando la página y qué requisitos previos que se va a incluir.  
  
 El nombre predeterminado de la página Web es Publish.htm; puede cambiar el nombre de la **Diseñador de proyectos**. Para obtener más información, consulte [Cómo: especificar una página de publicación para una aplicación ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).  
  
 Se publica la página Publish.htm Web sólo si se detecta una versión más reciente.  
  
> [!NOTE]
>  Los cambios que realice en su **publicar** configuración no afectará a la página Publish.htm, con una excepción: si agrega o quita los requisitos previos después de publicar inicialmente, la lista de requisitos previos ya no será precisa. Deberá editar el texto del vínculo de requisitos previos reflejar los cambios.  
  
### <a name="to-customize-the-publish-web-page"></a>Para personalizar la página Web de publicación  
  
1.  Publicar la aplicación ClickOnce para una ubicación Web. Para obtener más información, consulte [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
2.  En el servidor Web, abra el archivo Publish.htm en el Diseñador Web Visual u otro editor de HTML.  
  
3.  Personalizar la página según sea necesario y guárdelo.  
  
4.  Opcional. Para evitar que Visual Studio sobrescriba la página Web de publicación personalizada, desactive la opción **generar automáticamente la página web de implementación después de cada publicación** en el cuadro de diálogo Opciones de publicación.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Instalar requisitos previos mediante una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Cómo: Especificar una página de publicación para una aplicación ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)



