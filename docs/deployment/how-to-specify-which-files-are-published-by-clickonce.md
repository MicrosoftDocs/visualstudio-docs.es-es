---
title: "C&#243;mo: Especificar los archivos que se van a publicar mediante ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.VisualStudio.Publish.BaseProvider.Dialog.File"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implementación ClickOnce, exclusión de archivos"
  - "archivos, publicar mediante ClickOnce"
ms.assetid: 579c134a-d50f-4e0c-8e05-2a4ff654896a
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# C&#243;mo: Especificar los archivos que se van a publicar mediante ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando se publica una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], todos los archivos sin código en el proyecto se implementan junto con la aplicación.  En algunos casos, puede que no desee ni necesite publicar algunos archivos o puede que desee instalar algunos archivos según las condiciones.  Visual Studio proporciona las funciones para excluir los archivos, marcarlos como archivos de datos o requisitos previos y crear grupos para la instalación condicional.  
  
 Los archivos de una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se administran en el cuadro de diálogo **Archivos de aplicación**, al que se puede obtener acceso desde la página **Publicar** del **Diseñador de proyectos**.  
  
 Inicialmente, hay un solo grupo de archivos denominado **\(Requerido\)**.  Puede crear grupos de archivos adicionales y asignarles archivos.  No se puede cambiar el **Grupo de descarga** de los archivos que se requieren para ejecutar la aplicación.  Por ejemplo, el archivo .exe de la aplicación o los archivos marcados como archivos de datos deben pertenecer al grupo **\(Requerido\)**.  
  
 El valor predeterminado del estado de publicación de un archivo se etiqueta como **\(Automático\)**.  Por ejemplo, el archivo .exe de la aplicación tiene, de manera predeterminada, un estado de publicación de **Incluir \(Automático\)**.  
  
 Los archivos cuya propiedad **Acción de compilación** está establecida en **Contenido** se designan como archivos de aplicación y se marcan como incluidos de forma predeterminada.  Dichos archivos se pueden incluir, excluir o marcar como archivos de datos.  Hay algunas excepciones:  
  
-   Los archivos de datos como los archivos de bases de datos SQL \(.mdf y .mdb\) y los archivos XML se marcarán de forma predeterminada como archivos de datos.  
  
-   Las referencias a ensamblados \(archivos .dll\) se designan de la siguiente forma cuando se agrega una referencia: si **Copia local** es **False**, se marca de forma predeterminada como un ensamblado de requisito previo \(**Requisito previo \(Automático\)**\) que debe estar presente en la GAC antes de instalar la aplicación.  Si **Copia local** es **True**, el ensamblado se marca de forma predeterminada como un ensamblado de aplicación \(**Incluir \(Automático\)**\) y se copiará en la carpeta de la aplicación durante la instalación.  Aparecerá una referencia COM en el cuadro de diálogo **Archivos de aplicación** \(como un archivo .ocx\) únicamente si la propiedad **Isolated** está establecida en **True**.  Se incluirá de forma predeterminada.  
  
### Para agregar archivos al cuadro de diálogo Archivos de aplicación  
  
1.  Seleccione un archivo de datos en el **Explorador de soluciones**.  
  
2.  En la ventana Propiedades, cambie la propiedad **Acción de compilación** al valor **Contenido**.  
  
### Para excluir los archivos de la publicación ClickOnce  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Haga clic en la ficha **Publicar**.  
  
3.  Haga clic en el botón **Archivos de aplicación** para abrir el cuadro de diálogo **Archivos de aplicación**.  
  
4.  En el cuadro de diálogo **Archivos de aplicación**, seleccione el archivo que desea excluir.  
  
5.  En el campo **Estado de la publicación**, seleccione **Excluir** en la lista desplegable.  
  
### Para marcar los archivos como archivos de datos  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Haga clic en la ficha **Publicar**.  
  
3.  Haga clic en el botón **Archivos de aplicación** para abrir el cuadro de diálogo **Archivos de aplicación**.  
  
4.  En el cuadro de diálogo **Archivos de aplicación**, seleccione el archivo que desea marcar como datos.  
  
5.  En el campo **Estado de la publicación**, seleccione **Archivo de datos** en la lista desplegable.  
  
### Para marcar archivos como requisitos previos  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Haga clic en la ficha **Publicar**.  
  
3.  Haga clic en el botón **Archivos de aplicación** para abrir el cuadro de diálogo **Archivos de aplicación**.  
  
4.  En el cuadro de diálogo **Archivos de aplicación**, seleccione el ensamblado de aplicación \(archivo .dll\) que desea marcar como requisito previo.  Observe que su aplicación debe tener una referencia al ensamblado de aplicación para que éste aparezca en la lista.  
  
5.  En el campo **Estado de la publicación**, seleccione **Requisitos previos** en la lista desplegable.  
  
### Para agregar un nuevo grupo de archivos  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Haga clic en la ficha **Publicar**.  
  
3.  Haga clic en el botón **Archivos de aplicación** para abrir el cuadro de diálogo **Archivos de aplicación**.  
  
4.  En el cuadro de diálogo **Archivos de aplicación**, seleccione el campo **Grupo** para incluir el archivo en el nuevo grupo.  
  
    > [!NOTE]
    >  Los archivos deben tener la propiedad **Acción de compilación** establecida en **Contenido** antes de que los nombres de archivo aparezcan en el cuadro de diálogo **Archivos de aplicación**.  
  
5.  En el campo **Grupo de descarga**, seleccione **\<Nuevo...\>** en la lista desplegable.  
  
6.  En el cuadro de diálogo **Nuevo grupo**, escriba un nombre para el grupo y, a continuación, haga clic en **Aceptar**.  
  
### Para agregar un archivo a un grupo  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Haga clic en la ficha **Publicar**.  
  
3.  Haga clic en el botón **Archivos de aplicación** para abrir el cuadro de diálogo **Archivos de aplicación**.  
  
4.  En el cuadro de diálogo **Archivos de aplicación**, seleccione el campo **Grupo** para incluir el archivo en el nuevo grupo.  
  
5.  En el campo **Grupo de descarga**, seleccione un grupo en la lista desplegable.  
  
    > [!NOTE]
    >  No se puede cambiar el **Grupo de descarga** de los archivos que se requieren para ejecutar la aplicación.  
  
## Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce sin usar el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)