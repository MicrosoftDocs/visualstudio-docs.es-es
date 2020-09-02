---
title: 'Cómo: cambiar el idioma de publicación para una aplicación ClickOnce | Microsoft Docs'
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
ms.openlocfilehash: 26e4074b731dad44cd9eed40f1c1cc755d786562
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683793"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Cómo: Cambiar el idioma de publicación de una aplicación ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al publicar una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación, la interfaz de usuario mostrada durante la instalación tiene como valor predeterminado el idioma y la referencia cultural del equipo de desarrollo. Si está publicando una aplicación localizada, deberá especificar un idioma y una referencia cultural para que coincida con la versión localizada. Esto viene determinado por la `Publish language` propiedad del proyecto.  
  
 La `Publish language` propiedad se puede establecer en el cuadro de diálogo **Opciones de publicación** , accesible desde la página **publicar** del **Diseñador de proyectos**.  
  
> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo de Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-change-the-publish-language"></a>Para cambiar el idioma de publicación  
  
1. Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2. Haga clic en la pestaña **Publicar**.  
  
3. Haga clic en el botón **Opciones** para abrir el cuadro de diálogo **Opciones de publicación** .  
  
4. Haga clic en **Descripción**.  
  
5. En el cuadro de diálogo **Opciones de publicación** , seleccione un idioma y una referencia cultural en la lista desplegable **idioma de publicación** y, a continuación, haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Consulte también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicación de una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
