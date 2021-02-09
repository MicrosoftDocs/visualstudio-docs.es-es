---
title: Personalizar la página web predeterminada para la aplicación ClickOnce
description: Obtenga información sobre la página web que se genera al publicar una aplicación ClickOnce en la web, que contiene el nombre de la aplicación y otra información.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0377bdc5fa38c814bb5cd6ff02d12dcec117266d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900788"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Cómo: Personalizar la página web predeterminada para una aplicación ClickOnce
Al publicar una aplicación ClickOnce en la web, se genera automáticamente una página web y se publica junto con la aplicación. La página predeterminada contiene el nombre de la aplicación y vínculos para instalar la aplicación, instalar los requisitos previos o tener acceso a la ayuda en MSDN.

> [!NOTE]
> Los vínculos reales que se ven en la página dependen del equipo en el que se está viendo la página y de los requisitos previos que se incluyen.

 El nombre predeterminado de la página web es *Publish.htm*; puede cambiar el nombre en el **Diseñador de proyectos**. Para obtener más información, vea [Cómo: especificar una página de publicación para una aplicación ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).

 La Página Web de *Publish.htm* se publica solo si se detecta una versión más reciente.

> [!NOTE]
> Los cambios que realice en la configuración de **publicación** no afectarán a la página *Publish.htm* , con una excepción: Si agrega o quita los requisitos previos después de la publicación inicial, la lista de requisitos previos ya no será exacta. Tendrá que editar el texto del vínculo de requisito previo para reflejar los cambios.

### <a name="to-customize-the-publish-web-page"></a>Para personalizar la Página Web de publicación

1. Publique la aplicación ClickOnce en una ubicación Web. Para obtener más información, consulte [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

2. En el servidor Web, abra el archivo de *Publish.htm* en Visual Web Designer u otro editor HTML.

3. Personalice la página como desee y guárdela.

4. Opcional. Para evitar que Visual Studio sobrescriba la Página Web de publicación personalizada, desactive la casilla **generar automáticamente la Página Web de implementación después de cada publicación** en el cuadro de diálogo **Opciones de publicación** .

## <a name="see-also"></a>Vea también
- [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Cómo: instalar los requisitos previos con una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Cómo: especificar una página de publicación para una aplicación ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)