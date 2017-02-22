---
title: "C&#243;mo: Especificar un nombre en el men&#250; Inicio para una aplicaci&#243;n ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "implementación ClickOnce, nombre del menú Inicio"
  - "nombre del menú Inicio"
  - "nombre del recurso del menú Inicio"
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Especificar un nombre en el men&#250; Inicio para una aplicaci&#243;n ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se instala para utilizarla con y sin conexión, se agrega una entrada al menú **Inicio** y a la lista **Agregar o quitar programas**.  De forma predeterminada, el nombre que se muestra es el mismo que el del ensamblado de aplicación, pero se puede cambiar en **Nombre de producto**, en el cuadro de diálogo **Opciones de publicación**.  
  
 En la página publish.htm aparecerá **Nombre del producto**; en el caso de aplicaciones instaladas sin conexión, será el nombre de la entrada que aparece en el menú **Inicio**, además del nombre que aparece en **Agregar o quitar programas**.  
  
 En la página publish.htm, encima de **Nombre del producto**, aparecerá **Nombre del publicador** y, para las aplicaciones instaladas sin conexión, también será el nombre de la carpeta que contiene el icono de la aplicación en el menú **Inicio**.  
  
 Puede establecer las propiedades **Nombre del producto** y **Nombre del publicador** en el cuadro de diálogo **Opciones de publicación**, disponible en la página **Publicar** del **Diseñador de proyectos**.  
  
### Para especificar un nombre del menú Inicio  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Haga clic en la ficha **Publicar**.  
  
3.  Haga clic en el botón **Opciones** para abrir el cuadro de diálogo **Opciones de publicación**.  
  
4.  Haga clic en **Descripción**.  
  
5.  En el cuadro de diálogo **Opciones de publicación**, escriba el nombre para mostrar en el campo **Nombre del producto**.  
  
6.  Opcionalmente, puede escribir un nombre de publicador en **Nombre del publicador**.  
  
## Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce sin usar el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)