---
title: Publicar aplicaciones ClickOnce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Options
- Microsoft.VisualStudio.Publish.ClickOnceProvider.PublishWizard.Help
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- ClickOnce applications, publishing
- applications [Visual Studio], ClickOnce deployment
- deploying applications [ClickOnce], publishing ClickOnce applications
ms.assetid: eb6dfe79-f54c-4331-8e36-073688e70973
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d0c6f931af213ff7ce97ec77c2b742d6767cf733
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079257"
---
# <a name="publish-clickonce-applications"></a>Publicar aplicaciones ClickOnce
Cuando se publica una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] por primera vez, las propiedades de publicación se pueden establecer con el Asistente para publicación. Sólo algunas de las propiedades están disponibles en el asistente; todas las restantes se establecen en sus valores predeterminados.  
  
 Los cambios posteriores en las propiedades de publicación se realizan en el **publicar** página en el **Diseñador de proyectos**.  
  
## <a name="publish-wizard"></a>Asistente para publicación  
 Puede utilizar el Asistente para publicación para definir la configuración básica de la publicación. Incluye las siguientes propiedades de publicación:  
  
-   Ubicación de la carpeta de publicación: es la ubicación donde Visual Studio va a copiar los archivos (equipo local, recurso compartido de archivos de la red, servidor FTP o sitio web).  
  
-   Ubicación de la carpeta de instalación: es la ubicación desde donde los usuarios finales van a realizar la instalación (recurso compartido de archivos de la red, servidor FTP, sitio web, CD/DVD)  
  
-   Disponibilidad en línea o sin conexión: determina si los usuarios pueden obtener acceso a la aplicación con o sin conexión a la red.  
  
-   Frecuencia de actualización: define la frecuencia con la que la aplicación comprueba si hay nuevas actualizaciones.  
  
 Para obtener más información, consulte [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
## <a name="publish-page"></a>Página Publicar  
 La página **Publicar** del **Diseñador de proyectos** se utiliza para configurar las propiedades para la implementación de ClickOnce. En la tabla siguiente se enumera los temas.  
  
|Title|Descripción|  
|-----------|-----------------|  
|[Cómo: especificar dónde Visual Studio copia los archivos](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)|Describe cómo establecer la ubicación donde Visual Studio copia los archivos de aplicación y los manifiestos.|  
|[Cómo: especificar la ubicación donde se instalarán los usuarios finales desde](../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)|Describe cómo establecer la ubicación desde donde los usuarios van a descargar e instalar la aplicación.|  
|[Cómo: especificar la sin conexión de ClickOnce o instalar el modo en línea](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)|Describe cómo establecer si la aplicación estará disponible sin conexión o en línea.|  
|[Cómo: establecer la publicación de ClickOnce versión](../deployment/how-to-set-the-clickonce-publish-version.md)|Describe cómo establecer el ClickOnce **Publicar versión** propiedad, que determina si la aplicación que se está publicando se tratará como una actualización.|  
|[Cómo: incrementar automáticamente la ClickOnce publicación de versión](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)|Describe cómo incrementar automáticamente el número de revisión de la **PublishVersion** cada vez publique la aplicación.|  
  
 Para obtener más información, consulte [página Publicar, Diseñador de proyectos](../ide/reference/publish-page-project-designer.md)  
  
### <a name="application-files-dialog-box"></a>Cuadro de diálogo de archivos de aplicación  
 Este cuadro de diálogo le permite especificar cómo se organizan en categorías los archivos de su proyecto para la publicación, la descarga dinámica y la actualización. Contiene una cuadrícula que muestra los archivos de proyecto que no se excluyen de manera predeterminada o que tienen un grupo de descarga.  
  
 Para excluir archivos, marcarlos como archivos de datos o los requisitos previos y crear grupos de archivos para la instalación condicional en la IU de Visual Studio, consulte [Cómo: especificar qué archivos se publican mediante ClickOnce](../deployment/how-to-specify-which-files-are-published-by-clickonce.md). Los archivos de datos también se pueden marcar mediante la herramienta Mage.exe. Para obtener más información, consulte [Cómo: incluir un archivo de datos en una aplicación ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
### <a name="prerequisites-dialog-box"></a>Cuadro de diálogo Requisitos previos  
 Este cuadro de diálogo especifica qué componentes necesarios se instalan y cómo se instalan. Para obtener más información, consulte [Cómo: instalar requisitos previos mediante una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) y [cuadro de diálogo de requisitos previos](../ide/reference/prerequisites-dialog-box.md).  
  
### <a name="application-updates-dialog-box"></a>Cuadro de diálogo de las actualizaciones de aplicación  
 Este cuadro de diálogo especifica cómo debe comprobar la instalación de la aplicación si hay actualizaciones. Para obtener más información, consulte [Cómo: administrar las actualizaciones de una aplicación ClickOnce](../deployment/how-to-manage-updates-for-a-clickonce-application.md).  
  
### <a name="publish-options-dialog-box"></a>Cuadro de diálogo Opciones de publicación  
 El cuadro de diálogo Opciones de publicación especifica las opciones de implementación de una aplicación.  
  
|||  
|-|-|  
|[Cómo: cambiar el idioma de publicación para una aplicación ClickOnce](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)|Describe cómo especificar un idioma y una referencia cultural para la versión localizada.|  
|[Cómo: especificar un nombre de menú de inicio para una aplicación ClickOnce](../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)|Describe cómo cambiar el nombre para mostrar de una aplicación ClickOnce.|  
|[Cómo: especificar un vínculo para soporte técnico](../deployment/how-to-specify-a-link-for-technical-support.md)|Describe cómo establecer el **dirección URL de soporte** propiedad, que identifica una página Web o recurso compartido de archivos donde los usuarios pueden ir para obtener información acerca de la aplicación.|  
|[Cómo: especificar una dirección URL de soporte para requisitos previos individuales en una implementación de ClickOnce](../deployment/how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment.md)|Explica cómo modificar manualmente un manifiesto de aplicación para incluir las direcciones URL de soporte de cada requisito previo.|  
|[Cómo: especificar una página de publicación para una aplicación ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)|Describe cómo generar y publicar una página web predeterminada (publish.htm) junto con la aplicación.|  
|[Cómo: personalizar la página Web predeterminada de ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)|Describe cómo personalizar la página web que se genera y se publica automáticamente junto con la aplicación.|  
|[Cómo: habilitar AutoStart para instalaciones con CD](../deployment/how-to-enable-autostart-for-cd-installations.md)|Describe cómo habilitar Autoinicio para que la aplicación ClickOnce se inicie automáticamente cuando se inserta el disco.|  
  
## <a name="related-tpics"></a>Tpics relacionados  
  
|Title|Descripción|  
|-----------|-----------------|  
|[Cómo: crear asociaciones de archivo de aplicación para unas ClickOnce](../deployment/how-to-create-file-associations-for-a-clickonce-application.md)|Describe cómo agregar a una aplicación ClickOnce compatibilidad con extensiones de nombre de archivo.|  
|[Cómo: recuperar información de la cadena de consulta en una aplicación ClickOnce en línea](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)|Muestra cómo recuperar los parámetros pasados a la dirección URL utilizada para ejecutar una aplicación ClickOnce.|  
|[Cómo: deshabilitar la activación de direcciones URL de aplicaciones ClickOnce mediante el diseñador](../deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer.md)|Describe cómo obligar a los usuarios para iniciar la aplicación desde el **iniciar** menú mediante el diseñador.|  
|[Cómo: deshabilitar la activación de direcciones URL de aplicaciones ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)|Describe cómo obligar a los usuarios para iniciar la aplicación desde el **iniciar** menú.|  
|[Tutorial: Descargar ensamblados a petición con la API mediante el Diseñador de implementación de ClickOnce](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)|Explica cómo descargar los ensamblados de aplicación solo cuando la aplicación los utiliza por primera vez mediante el diseñador.|  
|[Tutorial: Descargar ensamblados a petición con la API de implementación de ClickOnce](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Explica cómo descargar los ensamblados de aplicación sólo cuando la aplicación los utiliza por primera vez.|  
|[Tutorial: Descargar ensamblados satélite a petición con la API de implementación de ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Describe cómo marcar los ensamblados satélite como opcionales y descargar únicamente el ensamblado que un equipo cliente necesite para la configuración de su referencia cultural actual.|  
|[Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)|Explica cómo utilizar las utilidades de .NET Framework para implementar su aplicación ClickOnce.|  
|[Tutorial: Implementar manualmente una aplicación ClickOnce que no requiere volver a firmar y que conserve la información de personalización de marca](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)|Explica cómo utilizar las utilidades de .NET Framework para implementar la aplicación ClickOnce sin volver a firmar los manifiestos.|  
|[Cómo: configurar proyectos para plataformas de destino](../ide/how-to-configure-projects-to-target-platforms.md)|Explica cómo publicar para un procesador de 64 bits, cambie el **CPU de destino** o **destino de la plataforma** propiedad en el proyecto.|  
|[Tutorial: Habilitar una aplicación ClickOnce para ejecutarse en varias versiones de .NET Framework](http://msdn.microsoft.com/en-us/7f4383af-ed87-4853-b4d4-02a3967a5fd9)|Explica cómo habilitar una aplicación ClickOnce para que se instale y se ejecute en varias versiones de .NET Framework.|  
|[Tutorial: Crear a un instalador personalizado para una aplicación ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)|Explica cómo crear un instalador personalizado para instalar una aplicación ClickOnce.|  
|[Cómo: publicar una aplicación WPF con estilos visuales habilitados](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)|Proporciona instrucciones paso a paso para resolver un error que se produce al intentar publicar una aplicación WPF que tiene habilitados estilos visuales.|  
  
## <a name="see-also"></a>Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Referencia de ClickOnce](../deployment/clickonce-reference.md)