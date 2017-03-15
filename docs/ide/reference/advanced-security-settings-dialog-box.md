---
title: "Configuraci&#243;n de seguridad avanzada (Cuadro de di&#225;logo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.err.debug_in_zone_no_hostproc"
  - "vs.err.debug_in_zone_no_hostproc:11310"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Cuadro de diálogo Configuración de seguridad avanzada"
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Configuraci&#243;n de seguridad avanzada (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Este cuadro de diálogo permite especificar la configuración de seguridad relacionada con la depuración en la zona.  
  
 Para tener acceso a este cuadro de diálogo, seleccione un nodo de proyecto en el **Explorador de soluciones** y, a continuación, en el menú **Proyecto** haga clic en **Propiedades**.  Cuando aparezca el **Diseñador de proyectos**, haga clic en la ficha **Seguridad**.  En la página **Seguridad**, haga clic sucesivamente en **Habilitar configuración de seguridad de ClickOnce**, **Aplicación de confianza parcial** y **Avanzada**.  
  
## Lista de UIElement  
 **Depurar esta aplicación con el conjunto de permisos seleccionados**  
 Si activa esta casilla, el conjunto de permisos seleccionado en la página **Seguridad** se utiliza durante la depuración.  Esta opción se encuentra activada de forma predeterminada.  
  
 Para que funcione la depuración en una zona de seguridad, esta opción debe estar habilitada. También debe estarlo la opción **Habilitar el proceso de alojamiento de Visual Studio**, disponible en la página **Depurar** del **Diseñador de proyectos**.  
  
 Para los proyectos de aplicación de explorador web de WPF, la opción **Depurar esta aplicación con el conjunto de permisos seleccionados** está activada y deshabilitada.  
  
 **Conceder acceso a la aplicación al sitio de origen**  
 Si activa esta casilla, la aplicación puede tener acceso al sitio web o recurso compartido del servidor en el que se publica.  Esta opción se encuentra activada de forma predeterminada.  
  
 **Depurar esta aplicación como si se hubiera descargado de la siguiente dirección URL**  
 Si tiene que permitir que la aplicación tenga acceso al sitio web o al recurso compartido de red correspondiente a la **Dirección URL de instalación** especificada en la página **Publicar**, escriba aquí esa dirección URL.  Esta opción sólo está disponible cuando se selecciona **Conceder acceso a la aplicación al sitio de origen**.  
  
## Vea también  
 [Página Seguridad, Diseñador de proyectos](../../ide/reference/security-page-project-designer.md)