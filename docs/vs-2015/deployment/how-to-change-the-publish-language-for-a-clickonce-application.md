---
title: Procedimiento Cambiar el idioma de publicación de una aplicación ClickOnce | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cac9d8ef6a8165b8fffd9e7f2be931828bb529f8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60081156"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Procedimiento Cambiar el idioma de publicación de una aplicación ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al publicar un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación, la interfaz de usuario que se muestran durante la instalación el valor predeterminado es el idioma y la referencia cultural del equipo de desarrollo. Si va a publicar una aplicación localizada, deberá especificar un idioma y referencia cultural para que coincida con la versión localizada. Esto viene determinado por la `Publish language` propiedad para el proyecto.  
  
 El `Publish language` propiedad puede establecerse el **opciones de publicación** cuadro de diálogo, accesible desde el **publicar** página de la **Diseñador de proyectos**.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-change-the-publish-language"></a>Para cambiar el idioma de publicación  
  
1. Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2. Haga clic en la pestaña **Publicar**.  
  
3. Haga clic en el **opciones** botón para abrir el **opciones de publicación** cuadro de diálogo.  
  
4. Haga clic en **descripción**.  
  
5. En el **opciones de publicación** diálogo cuadro, seleccione un idioma y referencia cultural de la **idioma de publicación** lista desplegable y, a continuación, haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicación de una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
