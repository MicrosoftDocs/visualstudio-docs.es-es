---
title: Especificar archivos para publicar (ClickOnce)
description: Obtenga información acerca de cómo excluir archivos, marcar archivos como archivos de datos o requisitos previos, y crear grupos para la instalación condicional de una aplicación ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d093438dc30bee08abbc45c6cf3c2555fbe208c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887489"
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>Cómo: Especificar los archivos que se van a publicar mediante ClickOnce
Al publicar una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación, todos los archivos que no son de código del proyecto se implementan junto con la aplicación. En algunos casos, es posible que no desee o necesite publicar determinados archivos, o puede que desee instalar determinados archivos en función de las condiciones. Visual Studio proporciona las capacidades para excluir archivos, marcar archivos como archivos de datos o requisitos previos, y crear grupos de archivos para la instalación condicional.

 Los archivos de una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación se administran en el cuadro de diálogo **archivos de aplicación** , accesible desde la página **publicar** del **Diseñador de proyectos**.

 Inicialmente, hay un único grupo de archivos denominado **(obligatorio)**. Puede crear grupos de archivos adicionales y asignarles archivos. No se puede cambiar el **grupo de descarga** de los archivos necesarios para que se ejecute la aplicación. Por ejemplo, el archivo. exe de la aplicación o los archivos marcados como archivos de datos deben pertenecer al grupo **(obligatorio)** .

 El valor predeterminado de estado de publicación de un archivo se etiqueta con **(auto)**. Por ejemplo, el archivo. exe de la aplicación tiene un estado de publicación de **incluir (auto)** de forma predeterminada.

 Los archivos con la propiedad **acción de compilación** establecida en **contenido** se designan como archivos de aplicación y se marcarán como incluidos de forma predeterminada. Se pueden incluir, excluir o marcar como archivos de datos. Las excepciones son las siguientes:

- De forma predeterminada, los archivos de datos, como los archivos de SQL Database (*. MDF* y *. mdb*) y los archivos XML, se marcarán como archivos de datos.

- Las referencias a los ensamblados (archivos *. dll* ) se designan como se indica a continuación al agregar la referencia: Si **Copy local** es **false**, se marca de forma predeterminada como un ensamblado de requisito previo (**requisito previo (auto)**) que debe estar presente en la GAC antes de que se instale la aplicación. Si **Copy local** es **true**, el ensamblado está marcado de forma predeterminada como un ensamblado de aplicación (**include (auto)**) y se copiará en la carpeta de la aplicación durante la instalación. Aparecerá una referencia COM en el cuadro de diálogo **archivos de aplicación** (como un archivo *. ocx* ) solo si su propiedad **aislada** está establecida en **true**. De forma predeterminada, se incluirá.

### <a name="to-add-files-to-the-application-files-dialog-box"></a>Para agregar archivos al cuadro de diálogo archivos de aplicación

1. Seleccione un archivo de datos en **Explorador de soluciones**.

2. En el ventana Propiedades, cambie la propiedad **acción de compilación** al valor **contenido** .

### <a name="to-exclude-files-from-clickonce-publishing"></a>Para excluir archivos de la publicación ClickOnce

1. Seleccione un proyecto en el **Explorador de soluciones** y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Publicar**.

3. Haga clic en el botón **archivos de aplicación** para abrir el cuadro de diálogo **archivos de aplicación** .

4. En el cuadro de diálogo **archivos de aplicación** , seleccione el archivo que desea excluir.

5. En el campo **Estado de publicación** , seleccione **excluir** en la lista desplegable.

### <a name="to-mark-files-as-data-files"></a>Para marcar archivos como archivos de datos

1. Seleccione un proyecto en el **Explorador de soluciones** y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Publicar**.

3. Haga clic en el botón **archivos de aplicación** para abrir el cuadro de diálogo **archivos de aplicación** .

4. En el cuadro de diálogo **archivos de aplicación** , seleccione el archivo que desea marcar como datos.

5. En el campo **Estado de publicación** , seleccione Archivo de **datos** en la lista desplegable.

### <a name="to-mark-files-as-prerequisites"></a>Para marcar archivos como requisitos previos

1. Seleccione un proyecto en el **Explorador de soluciones** y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Publicar**.

3. Haga clic en el botón **archivos de aplicación** para abrir el cuadro de diálogo **archivos de aplicación** .

4. En el cuadro de diálogo **archivos de aplicación** , seleccione el ensamblado de la aplicación (archivo *. dll* ) que desea marcar como requisito previo. Tenga en cuenta que la aplicación debe tener una referencia al ensamblado de la aplicación para que aparezca en la lista.

5. En el campo **Estado de publicación** , seleccione **requisito previo** en la lista desplegable.

### <a name="to-add-a-new-file-group"></a>Para agregar un nuevo grupo de archivos

1. Seleccione un proyecto en el **Explorador de soluciones** y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Publicar**.

3. Haga clic en el botón **archivos de aplicación** para abrir el cuadro de diálogo **archivos de aplicación** .

4. En el cuadro de diálogo **archivos de aplicación** , seleccione el campo de **Grupo** de un archivo que desea incluir en el nuevo grupo.

    > [!NOTE]
    > Los archivos deben tener la propiedad **acción de compilación** establecida en **contenido** antes de que aparezcan los nombres de archivo en el cuadro de diálogo **archivos de aplicación** .

5. En el campo **grupo de descarga** , seleccione **\<New...>** en la lista desplegable.

6. En el cuadro de diálogo **nuevo grupo** , escriba un nombre para el grupo y, a continuación, haga clic en **Aceptar**.

### <a name="to-add-a-file-to-a-group"></a>Para agregar un archivo a un grupo

1. Seleccione un proyecto en el **Explorador de soluciones** y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Publicar**.

3. Haga clic en el botón **archivos de aplicación** para abrir el cuadro de diálogo **archivos de aplicación** .

4. En el cuadro de diálogo **archivos de aplicación** , seleccione el campo de **Grupo** de un archivo que desea incluir en el nuevo grupo.

5. En el campo **grupo de descarga** , seleccione un grupo de la lista desplegable.

    > [!NOTE]
    > No se puede cambiar el **grupo de descarga** de los archivos necesarios para que se ejecute la aplicación.

## <a name="see-also"></a>Vea también
- [Publicación de aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)