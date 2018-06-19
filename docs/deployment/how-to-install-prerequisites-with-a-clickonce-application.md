---
title: 'Cómo: instalar requisitos previos mediante una aplicación ClickOnce | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], prerequisites
- prerequisites, ClickOnce
- components, bootstrapping
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d803ae651d75dd6195e4046b86a77d46d3174fc4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
ms.locfileid: "31559340"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Cómo: Instalar requisitos previos mediante una aplicación ClickOnce
Todos los [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicaciones requieren que esté instalada la versión correcta de .NET Framework en un equipo antes de poder ejecutar; muchas aplicaciones tienen además otros requisitos previos. Al publicar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación, puede elegir un conjunto de componentes de requisitos previos para empaquetar junto con la aplicación. Durante la instalación, se realizará una comprobación de todos los requisitos previos determinar si ya existe; Si no se instalará antes de instalar el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación.  
  
 En lugar de empaquetar y publicar los requisitos previos, también puede especificar una ubicación de descarga de los componentes. Por ejemplo, en lugar de incluir requisitos previos con todas las aplicaciones que se publican, puede usar un recurso compartido de archivos centralizado o ubicación Web que contenga los instaladores para todos los requisitos previos, durante la instalación, se descargarán los componentes y instalada desde esa ubicación.  
  
> [!IMPORTANT]
>  Debe agregar los paquetes de instalador de requisitos previos para el equipo de desarrollo antes de publicar su primer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. Para obtener más información, consulte [Cómo: incluir requisitos previos mediante una aplicación ClickOnce](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).  
  
 Requisitos previos se administran en el **requisitos previos** cuadro de diálogo, accesible desde el **publicar** panel de la **Diseñador de proyectos**.  
  
> [!NOTE]
>  Además de la lista predeterminada de requisitos previos, puede agregar sus propios componentes a la lista. Para obtener más información, consulte [crear paquetes de arranque](../deployment/creating-bootstrapper-packages.md).  
  
### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>Para especificar los requisitos previos para instalar con una aplicación ClickOnce  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Seleccione el **publicar** panel.  
  
3.  Haga clic en el **requisitos previos** para abrir el **requisitos previos** cuadro de diálogo.  
  
4.  En el cuadro de diálogo **Requisitos previos** , asegúrese de que está activada la casilla **Crear programa de instalación para instalar los componentes necesarios** .  
  
5.  En el **requisitos previos** lista, compruebe los componentes que desea instalar y, a continuación, haga clic en **Aceptar**.  
  
     Los componentes seleccionados se empaqueta y se publican junto con la aplicación.  
  
### <a name="to-specify-a-different-download-location-for-prerequisites"></a>Para especificar una ubicación de descarga diferente para los requisitos previos  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Seleccione el **publicar** panel.  
  
3.  Haga clic en el **requisitos previos** para abrir el **requisitos previos** cuadro de diálogo.  
  
4.  En el cuadro de diálogo **Requisitos previos** , asegúrese de que está activada la casilla **Crear programa de instalación para instalar los componentes necesarios** .  
  
5.  En el **especificar la ubicación de instalación de requisitos previos** sección, seleccione **descargar los requisitos previos de la siguiente ubicación**.  
  
6.  Seleccione una ubicación en la lista desplegable, o escriba una dirección URL, la ruta de acceso de archivo o la ubicación FTP y, a continuación, haga clic en **Aceptar.**  
  
    > [!NOTE]
    >  Debe asegurarse de que los instaladores para los componentes especificados existen en la ubicación especificada.  
  
## <a name="see-also"></a>Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)