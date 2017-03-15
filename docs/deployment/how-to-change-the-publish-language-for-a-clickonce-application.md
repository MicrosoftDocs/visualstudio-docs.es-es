---
title: "C&#243;mo: Cambiar el idioma de publicaci&#243;n de una aplicaci&#243;n ClickOnce | Microsoft Docs"
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
  - "implementación ClickOnce, cambiar lenguaje de publicación"
  - "propiedad de lenguaje de publicación"
  - "publicar, ClickOnce"
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# C&#243;mo: Cambiar el idioma de publicaci&#243;n de una aplicaci&#243;n ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Al publicar una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], la interfaz de usuario mostró los valores predeterminados del idioma y la referencia cultural del equipo de desarrollo durante la instalación.  Si publica una aplicación adaptada, necesitará especificar un idioma y una referencia cultural que coincidan con la versión adaptada.  La propiedad `Publish language` del proyecto determina esta información.  
  
 La propiedad `Publish language` se puede establecer en el cuadro de diálogo **Opciones de publicación**, al que se tiene acceso desde la página **Publicar** del **Diseñador de proyectos**.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Para cambiar el idioma de publicación  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Haga clic en la ficha **Publicar**.  
  
3.  Haga clic en el botón **Opciones** para abrir el cuadro de diálogo **Opciones de publicación**.  
  
4.  Haga clic en **Descripción**.  
  
5.  En el cuadro de diálogo **Opciones de publicación**, seleccione un idioma y una referencia cultural de la lista desplegable **Idioma de publicación** y, a continuación, haga clic en **Aceptar**.  
  
## Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce sin usar el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)