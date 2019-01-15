---
title: Procedimiento Especificar qué archivos se publican mediante ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.File
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, file exclusion
- files, publishing via ClickOnce
ms.assetid: 579c134a-d50f-4e0c-8e05-2a4ff654896a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e11c336f891ae71968a3b325a66a50d4d9a79446
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826960"
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>Procedimiento Especificación de los archivos que se van a publicar mediante ClickOnce
Al publicar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] archivos de aplicación, que no son código en el proyecto se implementan junto con la aplicación. En algunos casos, es posible que no desea o necesita publicar determinados archivos, o desea instalar determinados archivos según las condiciones. Visual Studio proporciona las capacidades para excluir archivos, marcar archivos como archivos de datos o los requisitos previos y crear grupos de archivos para la instalación condicional.  
  
 Los archivos de un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación se administran en el **archivos de la aplicación** cuadro de diálogo, accesible desde el **publicar** página de la **Diseñador de proyectos**.  
  
 Inicialmente, hay un solo grupo de archivos denominado **(obligatorio)**. Puede crear grupos de archivos adicionales y asignarles archivos. No puede cambiar el **grupo de descarga** para los archivos que son necesarios para ejecutar la aplicación. Por ejemplo, .exe de la aplicación o los archivos marcan como archivos de datos deben pertenecer a la **(obligatorio)** grupo.  
  
 El valor predeterminado de estado de publicación tiene una etiqueta con el valor de un archivo **(Auto)**. Por ejemplo, .exe de la aplicación tiene un estado de publicación de **incluir (automático)** de forma predeterminada.  
  
 Los archivos con la **acción de compilación** propiedad establecida en **contenido** se designan como archivos de aplicación y se marcará como incluye de forma predeterminada. Pueden incluidos, excluidos o marcados como archivos de datos. Las excepciones son los siguientes:  
  
-   Archivos de datos como base de datos SQL (*.mdf* y *.mdb*) archivos y archivos XML se marcará como archivos de datos de forma predeterminada.  
  
-   Referencias a ensamblados (*.dll* archivos) se designan como se indica a continuación, al agregar la referencia: Si **Copy Local** es **False**, está marcada de forma predeterminada como un ensamblado de requisito previo (**requisito previo (Auto)**) que debe estar presente en la GAC antes de instalar la aplicación. Si **Copy Local** es **True**, el ensamblado está marcado como un ensamblado de aplicación de forma predeterminada (**incluir (automático)**) y se copiará en la carpeta de la aplicación durante la instalación. Una referencia COM aparecerá en el **archivos de la aplicación** cuadro de diálogo (como un *.ocx* archivo) solo si su **aislado** propiedad está establecida en **True**. De forma predeterminada, se incluirá.  
  
### <a name="to-add-files-to-the-application-files-dialog-box"></a>Para agregar archivos al cuadro de diálogo archivos de aplicación  
  
1.  Seleccione un archivo de datos en **el Explorador de soluciones**.  
  
2.  En la ventana Propiedades, cambie la **acción de compilación** propiedad a la **contenido** valor.  
  
### <a name="to-exclude-files-from-clickonce-publishing"></a>Para excluir archivos de publicación de ClickOnce  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en la pestaña **Publicar**.  
  
3.  Haga clic en el **archivos de la aplicación** botón para abrir el **archivos de la aplicación** cuadro de diálogo.  
  
4.  En el **archivos de la aplicación** cuadro de diálogo, seleccione el archivo que desea excluir.  
  
5.  En el **estado de la publicación** campos, seleccione **excluir** en la lista desplegable.  
  
### <a name="to-mark-files-as-data-files"></a>Para marcar los archivos como archivos de datos  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en la pestaña **Publicar**.  
  
3.  Haga clic en el **archivos de la aplicación** botón para abrir el **archivos de la aplicación** cuadro de diálogo.  
  
4.  En el **archivos de la aplicación** cuadro de diálogo, seleccione el archivo que desea marcar como datos.  
  
5.  En el **estado de la publicación** campos, seleccione **archivo de datos** en la lista desplegable.  
  
### <a name="to-mark-files-as-prerequisites"></a>Para marcar los archivos como requisitos previos  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en la pestaña **Publicar**.  
  
3.  Haga clic en el **archivos de la aplicación** botón para abrir el **archivos de la aplicación** cuadro de diálogo.  
  
4.  En el **archivos de la aplicación** cuadro de diálogo, seleccione el ensamblado de aplicación (*.dll* archivo) que desea marcar como requisito previo. Tenga en cuenta que la aplicación debe tener una referencia al ensamblado de la aplicación en orden para que aparezca en la lista.  
  
5.  En el **estado de la publicación** campos, seleccione **requisitos previos** en la lista desplegable.  
  
### <a name="to-add-a-new-file-group"></a>Para agregar un nuevo grupo de archivos  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en la pestaña **Publicar**.  
  
3.  Haga clic en el **archivos de la aplicación** botón para abrir el **archivos de la aplicación** cuadro de diálogo.  
  
4.  En el **archivos de la aplicación** cuadro de diálogo, seleccione el **grupo** field para un archivo que desea incluir en el nuevo grupo.  
  
    > [!NOTE]
    >  Los archivos deben tener la **acción de compilación** propiedad establecida en **contenido** antes de que aparezcan los nombres de archivo en el **archivos de la aplicación** cuadro de diálogo.  
  
5.  En el **grupo de descarga** campos, seleccione  **\<nuevo... >** en la lista desplegable.  
  
6.  En el **nuevo grupo** cuadro de diálogo, escriba un nombre para el grupo y, a continuación, haga clic en **Aceptar**.  
  
### <a name="to-add-a-file-to-a-group"></a>Para agregar un archivo a un grupo  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en la pestaña **Publicar**.  
  
3.  Haga clic en el **archivos de la aplicación** botón para abrir el **archivos de la aplicación** cuadro de diálogo.  
  
4.  En el **archivos de la aplicación** cuadro de diálogo, seleccione el **grupo** field para un archivo que desea incluir en el nuevo grupo.  
  
5.  En el **grupo de descarga** , seleccione un grupo en la lista desplegable.  
  
    > [!NOTE]
    >  No puede cambiar el **grupo de descarga** para los archivos que son necesarios para ejecutar la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicación de una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)