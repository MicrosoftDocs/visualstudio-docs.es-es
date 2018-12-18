---
title: 'Cómo: instalar requisitos previos mediante una aplicación ClickOnce | Microsoft Docs'
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
ms.openlocfilehash: e363b021f8dfb82aa641a1baac4d2f33e0bd3d2e
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152479"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Cómo: instalar requisitos previos mediante una aplicación ClickOnce
Todos los [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicaciones requieren que la versión correcta de .NET Framework está instalada en un equipo antes de poder ejecutar; muchas aplicaciones tienen también otros requisitos previos. Al publicar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación, puede elegir un conjunto de componentes de requisitos previos pueden empaquetarse junto con la aplicación. Durante la instalación, se realizará una comprobación para que todos los requisitos previos determinar si ya existe; Si no se instalará antes de instalar el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación.  
  
 En lugar de empaquetar y publicar los requisitos previos, también puede especificar una ubicación de descarga de los componentes. Por ejemplo, en lugar de incluir requisitos previos con todas las aplicaciones que publique, puede usar un recurso compartido de archivos centralizado o la ubicación Web que contenga los instaladores para todos los requisitos previos, durante la instalación, se descargarán los componentes y instalada desde esa ubicación.  
  
> [!IMPORTANT]
>  Debe agregar los paquetes de instalador de requisitos previos para el equipo de desarrollo antes de publicar su primer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. Para obtener más información, consulte [Cómo: incluir requisitos previos mediante una aplicación ClickOnce](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).  
  
 Requisitos previos se administran en el **requisitos previos** cuadro de diálogo, accesible desde el **publicar** panel de la **Diseñador de proyectos**.  
  
> [!NOTE]
>  Además de la lista predeterminada de requisitos previos, puede agregar sus propios componentes a la lista. Para obtener más información, consulte [crear paquetes de arranque](../deployment/creating-bootstrapper-packages.md).  
  
### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>Para especificar los requisitos previos para instalar con una aplicación ClickOnce  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Seleccione el **publicar** panel.  
  
3.  Haga clic en el **requisitos previos** botón para abrir el **requisitos previos** cuadro de diálogo.  
  
4.  En el cuadro de diálogo **Requisitos previos** , asegúrese de que está activada la casilla **Crear programa de instalación para instalar los componentes necesarios** .  
  
5.  En el **requisitos previos** lista, compruebe los componentes que desea instalar y, a continuación, haga clic en **Aceptar**.  
  
     Los componentes seleccionados se empaquetan y publicar junto con la aplicación.  
  
### <a name="to-specify-a-different-download-location-for-prerequisites"></a>Para especificar una ubicación de descarga diferentes para los requisitos previos  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Seleccione el **publicar** panel.  
  
3.  Haga clic en el **requisitos previos** botón para abrir el **requisitos previos** cuadro de diálogo.  
  
4.  En el cuadro de diálogo **Requisitos previos** , asegúrese de que está activada la casilla **Crear programa de instalación para instalar los componentes necesarios** .  
  
5.  En el **especificar la ubicación de instalación de requisitos previos** sección, seleccione **descargar requisitos previos de la siguiente ubicación**.  
  
6.  Seleccione una ubicación en la lista desplegable o escriba una dirección URL, la ruta de acceso de archivo o la ubicación FTP y, a continuación, haga clic en **Aceptar.**  
  
    > [!NOTE]
    >  Debe asegurarse de que los instaladores para los componentes especificados existen en la ubicación especificada.  
  
## <a name="see-also"></a>Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)