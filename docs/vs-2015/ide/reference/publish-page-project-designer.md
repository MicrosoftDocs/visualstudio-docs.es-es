---
title: Panel Publicar, Diseñador de proyectos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Project Designer, Publish page
- Publish page in Project Designer
ms.assetid: 153527c6-8b95-4003-8e8e-03a489d0a629
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 15fd3f1b93378adba0579b6de50d0e779a09ac5a
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59658219"
---
# <a name="publish-page-project-designer"></a>Panel Publicar, Diseñador de proyectos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La página **Publicar** del **Diseñador de proyectos** se utiliza para configurar las propiedades para la implementación de ClickOnce.  
  
 Para tener acceso a la página **Publicar** , seleccione un nodo de proyecto en el **Explorador de soluciones**y, después, en el menú **Proyecto** , haga clic en **Propiedades**. Cuando se muestre el **Diseñador de proyectos** , haga clic en la pestaña **Publicar** .  
  
> [!NOTE]
>  Algunas de las propiedades de ClickOnce que se describen aquí también se pueden establecer en el **Asistente para publicación**, disponible en el menú **Compilación** o haciendo clic en el botón **Asistente para publicación** de esta página.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Ubicación de la carpeta de publicación**  
 Especifica la ubicación donde se publica la aplicación. Puede ser una ruta de acceso de unidad (`C:\deploy\myapplication`), un recurso compartido de archivos (`\\server\myapplication`), un servidor FTP (`ftp://ftp.microsoft.com/myapplication`) o un sitio web (`http://www.microsoft.com/myapplication`). Tenga en cuenta que debe haber texto en el cuadro **Ubicación de publicación** para que el botón Examinar (**...**) funcione.  
  
 De forma predeterminada, la ubicación de publicación es `http://localhost/<projectname>/` si tiene IIS instalado o el directorio `publish\` si no tiene IIS instalado. Si el equipo ejecuta Windows Vista, el valor predeterminado es siempre el directorio `publish\` , independientemente de si se tiene IIS instalado.  
  
 **Dirección URL de la carpeta de instalación**  
 Opcional. Especifica un sitio web adonde van los usuarios para instalar la aplicación. Solo es necesario cuando difiere de la **ubicación de publicación**, por ejemplo, cuando la aplicación se publica en un servidor de almacenamiento provisional.  
  
 **Modo y configuración de instalación**  
 Determina si la aplicación se ejecuta directamente desde la **ubicación de publicación** (cuando está seleccionado **La aplicación solo está disponible en línea** ) o si se instala y se agrega al menú **Inicio** y al elemento **Agregar o quitar programas** del **Panel de control** (cuando está seleccionado **La aplicación también está disponible sin conexión** ).  
  
 Para las aplicaciones de explorador web de WPF, la opción **La aplicación también está disponible sin conexión** está deshabilitada porque estas aplicaciones solo están disponibles en línea.  
  
 **Archivos de aplicación**  
 Abre el cuadro de diálogo [Archivos de aplicación](http://msdn.microsoft.com/b06dff3a-b87a-4caf-996b-7a4acf8137a8), que se usa para especificar cómo y dónde se instalan los archivos individuales.  
  
 **Requisitos previos**  
 Abre el cuadro de diálogo [Requisitos previos](../../ide/reference/prerequisites-dialog-box.md), que se usa para especificar los componentes necesarios, como .NET Framework, que se instalan junto con la aplicación.  
  
 **Actualizaciones**  
 Abre el cuadro de diálogo [Actualizaciones de la aplicación](http://msdn.microsoft.com/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f), que se usa para especificar el comportamiento de actualización de la aplicación. No está disponible cuando está seleccionado **La aplicación solo está disponible en línea** .  
  
 **Opciones**  
 Abre el cuadro de diálogo [Opciones de publicación](http://msdn.microsoft.com/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), que se usa para especificar otras opciones de publicación avanzadas.  
  
 **Versión de publicación**  
 Establece el número de versión de publicación de la aplicación. Cuando se cambia el número de versión, la aplicación se publica como una actualización. Cada parte de la versión de publicación (**Principal**, **Secundaria**, **Compilación** y **Revisión**) puede tener un valor máximo de 65 355 (<xref:System.UInt16.MaxValue>), que es el máximo que permite <xref:System.Version>.  
  
 Cuando se instala más de una versión de una aplicación con ClickOnce, la instalación mueve las versiones anteriores de la aplicación a una carpeta llamada Archivo, en la ubicación de publicación que especifiques. Al archivar las versiones anteriores de esta manera, el directorio de instalación se mantiene limpio de carpetas de versiones anteriores.  
  
 **Incrementar revisión automáticamente con cada publicación**  
 Opcional. Si esta opción está seleccionada (valor predeterminado), la parte **Revisión** del número de versión de publicación se incrementa en uno cada vez que se publica la aplicación. Esto hace que la aplicación se publique como una actualización.  
  
 **Asistente para publicación**  
 Abre el [Asistente para publicación](http://msdn.microsoft.com/fc6abebd-13d6-48e4-a567-fbc52dad0872). Finalizar el Asistente para publicación tiene el mismo efecto que ejecutar el comando **Publicar** en el menú **Compilación** .  
  
 **Publicar ahora**  
 Publica la aplicación mediante la configuración actual. Equivalente al botón **Finalizar** del **Asistente para publicación**.  
  
## <a name="see-also"></a>Vea también  
 [Publicar aplicaciones ClickOnce](../../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce mediante el Asistente para publicación](../../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Cómo: Especificar dónde Visual Studio copia los archivos](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Cómo: Especifique la ubicación donde se instalarán los usuarios finales desde](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)   
 [Cómo: Especifique un vínculo para soporte técnico](../../deployment/how-to-specify-a-link-for-technical-support.md)   
 [Cómo: Especifique el sin conexión de ClickOnce o instalar el modo en línea](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)   
 [Cómo: Habilitar AutoStart para instalaciones con CD](../../deployment/how-to-enable-autostart-for-cd-installations.md)   
 [Cómo: Establecer la publicación de ClickOnce versión](../../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Cómo: Automáticamente incrementar la publicación de ClickOnce versión](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Cómo: Especificar qué archivos son publicar mediante ClickOnce](../../deployment/how-to-specify-which-files-are-published-by-clickonce.md)   
 [Cómo: Instalar requisitos previos mediante una aplicación ClickOnce](../../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Cómo: Administrar actualizaciones de una aplicación ClickOnce](../../deployment/how-to-manage-updates-for-a-clickonce-application.md)   
 [Cómo: Cambiar el idioma de publicación de una aplicación ClickOnce](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)   
 [Cómo: Especifique un nombre de menú de inicio para una aplicación ClickOnce](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)   
 [Cómo: Especificar una página de publicación para una aplicación ClickOnce](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)   
 [Seguridad e implementación ClickOnce](../../deployment/clickonce-security-and-deployment.md)
