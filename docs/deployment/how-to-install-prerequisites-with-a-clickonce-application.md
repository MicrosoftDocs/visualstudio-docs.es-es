---
title: "C&#243;mo: Instalar requisitos previos mediante una aplicaci&#243;n ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "componentes, arranque"
  - "implementar aplicaciones [ClickOnce], requisitos previos"
  - "requisitos previos, ClickOnce"
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# C&#243;mo: Instalar requisitos previos mediante una aplicaci&#243;n ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Todas las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] requieren que esté instalada la versión correcta de .NET Framework en un equipo para que puedan ejecutarse; muchas aplicaciones tienen además otros requisitos previos.  Al publicar una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], puede elegir un conjunto de componentes que se empaquetarán como requisitos previos junto con la aplicación.  En el momento de la instalación, se realizará una comprobación de cada requisito previo para determinar si ya existe; si no existe, se instalará antes de que se instale la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 En lugar de empaquetar y publicar los requisitos previos, puede especificar también una ubicación de descarga para los componentes.  Por ejemplo, en vez de incluir requisitos previos con cada aplicación que publique, puede utilizar un recurso compartido de archivos o ubicación de Web centralizada que contenga los instaladores para todos los requisitos previos; en el momento de la instalación, los componentes se descargarán e instalarán desde esa ubicación.  
  
> [!IMPORTANT]
>  Debe agregar paquetes del instalador de requisitos previos para el equipo de desarrollo antes de publicar su primer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación.  Para obtener más información, vea [Cómo: Incluir requisitos previos mediante una aplicación ClickOnce](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).  
  
 Los requisitos previos se administran en el cuadro de diálogo **Requisitos previos**, accesible desde el panel **Publicar** del **Diseñador de proyectos**.  
  
> [!NOTE]
>  Además de la lista predeterminada de requisitos previos, puede agregar sus propios componentes a la lista.  Para obtener más información, vea [Crear paquetes de arranque](../deployment/creating-bootstrapper-packages.md).  
  
### Para especificar los requisitos previos que se instalarán con una aplicación ClickOnce  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Seleccione el panel **Publicar**.  
  
3.  Haga clic en el botón **Requisitos previos** para abrir el cuadro de diálogo **Requisitos previos**.  
  
4.  En el cuadro de diálogo **Requisitos previos**, asegúrese de que está activada la casilla **Crear programa de instalación para instalar los componentes necesarios**.  
  
5.  En la lista **Requisitos previos**, compruebe los componentes que desea instalar y, a continuación, haga clic en **Aceptar**.  
  
     Los componentes seleccionados se empaquetarán y publicarán junto con su aplicación.  
  
### Para especificar una ubicación de descarga diferente para los requisitos previos  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Seleccione el panel **Publicar**.  
  
3.  Haga clic en el botón **Requisitos previos** para abrir el cuadro de diálogo **Requisitos previos**.  
  
4.  En el cuadro de diálogo **Requisitos previos**, asegúrese de que está activada la casilla **Crear programa de instalación para instalar los componentes necesarios**.  
  
5.  En la sección **Especificar la ubicación de instalación de los requisitos previos**, seleccione **Descargar requisitos previos de la siguiente ubicación**.  
  
6.  Seleccione una ubicación en la lista desplegable o escriba una dirección URL, ruta de acceso del archivo o ubicación FTP y, a continuación, haga clic en **Aceptar**.  
  
    > [!NOTE]
    >  Asegúrese de que los instaladores para los componentes especificados existen en la ubicación especificada.  
  
## Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce sin usar el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)