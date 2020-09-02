---
title: Cómo instalar los requisitos previos con una aplicación ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce4ad97439d330a6fc51e741e9ea05ef53a5798a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382385"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Cómo: Instalar requisitos previos mediante una aplicación ClickOnce
Todas [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las aplicaciones requieren que se instale la versión correcta del .NET Framework en un equipo antes de poder ejecutarse; muchas aplicaciones tienen también otros requisitos previos. Al publicar una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación, puede elegir un conjunto de componentes de requisitos previos que se van a empaquetar junto con la aplicación. En el momento de la instalación, se realizará una comprobación para cada requisito previo para determinar si ya existe; Si no se instalará antes de instalar la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación.

 En lugar de empaquetar y publicar los requisitos previos, también puede especificar una ubicación de descarga para los componentes. Por ejemplo, en lugar de incluir requisitos previos con cada aplicación que publique, puede usar un recurso compartido de archivos o una ubicación web centralizados que contenga los instaladores para todos los requisitos previos: en el momento de la instalación, los componentes se descargarán e instalarán desde esa ubicación.

> [!IMPORTANT]
> Debe agregar los paquetes de instalador de requisitos previos al equipo de desarrollo antes de publicar la primera [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. Para obtener más información, vea [Cómo: incluir requisitos previos con una aplicación ClickOnce](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).

 Los requisitos previos se administran en el cuadro de diálogo **requisitos previos** , accesible desde el panel **publicar** del **Diseñador de proyectos**.

> [!NOTE]
> Además de la lista de requisitos previos predeterminada, puede agregar sus propios componentes a la lista. Para obtener más información, vea [crear paquetes de programa previo](../deployment/creating-bootstrapper-packages.md).

### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>Para especificar los requisitos previos para instalar con una aplicación ClickOnce

1. Con un proyecto seleccionado en **Explorador de soluciones**, en el menú **proyecto** , haga clic en **propiedades**.

2. Seleccione el panel **publicar** .

3. Haga clic en el botón **requisitos previos** para abrir el cuadro de diálogo **requisitos previos** .

4. En el cuadro de diálogo **Requisitos previos** , asegúrese de que está activada la casilla **Crear programa de instalación para instalar los componentes necesarios** .

5. En la lista de **requisitos previos** , compruebe los componentes que desea instalar y, a continuación, haga clic en **Aceptar**.

     Los componentes seleccionados se empaquetarán y publicarán junto con la aplicación.

### <a name="to-specify-a-different-download-location-for-prerequisites"></a>Para especificar una ubicación de descarga diferente para los requisitos previos

1. Con un proyecto seleccionado en **Explorador de soluciones**, en el menú **proyecto** , haga clic en **propiedades**.

2. Seleccione el panel **publicar** .

3. Haga clic en el botón **requisitos previos** para abrir el cuadro de diálogo **requisitos previos** .

4. En el cuadro de diálogo **Requisitos previos** , asegúrese de que está activada la casilla **Crear programa de instalación para instalar los componentes necesarios** .

5. En la sección **especificar la ubicación de instalación de los requisitos previos** , seleccione **Descargar requisitos previos de la siguiente ubicación**.

6. Seleccione una ubicación en la lista desplegable o escriba una dirección URL, una ruta de acceso de archivo o una ubicación FTP y, a continuación, haga clic en **Aceptar.**

    > [!NOTE]
    > Debe asegurarse de que los instaladores de los componentes especificados existen en la ubicación especificada.

## <a name="see-also"></a>Consulte también
- [Publicación de aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)