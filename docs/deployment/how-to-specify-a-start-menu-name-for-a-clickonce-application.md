---
title: 'Cómo: especificar un nombre de menú de inicio para una aplicación ClickOnce | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: a27adbd81db29b413bf85b2c7a465897eaeac987
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Cómo: Especificar un nombre en el menú Inicio para una aplicación ClickOnce
Cuando un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación está instalada para su uso en línea y sin conexión, se agrega una entrada para el **iniciar** menú y **agregar o quitar programas** lista. De forma predeterminada, el nombre para mostrar es el mismo que el nombre del ensamblado de aplicación, pero puede cambiar el nombre para mostrar estableciendo **nombre de producto** en el **opciones de publicación** cuadro de diálogo.  
  
 **Nombre de producto** se mostrará en la página publish.htm; para una aplicación instalada sin conexión, será el nombre de la entrada en el **iniciar** menú y, también será el nombre que se muestra en **agregar o quitar Programas**.  
  
 **Nombre del publicador** aparecerá en la página publish.htm anterior **nombre de producto**, y para una aplicación instalada sin conexión, también será el nombre de la carpeta que contiene el icono de la aplicación en el **iniciar**  menú.  
  
 Puede establecer la **nombre de producto** y **nombre del publicador** propiedades en el **opciones de publicación** cuadro de diálogo, disponible en la **publicar** página de la **Diseñador de proyectos**.  
  
### <a name="to-specify-a-start-menu-name"></a>Para especificar un nombre de menú de inicio  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en el **publicar** ficha.  
  
3.  Haga clic en el **opciones** para abrir el **opciones de publicación** cuadro de diálogo.  
  
4.  Haga clic en **descripción**.  
  
5.  En el **opciones de publicación** diálogo cuadro, escriba el nombre para mostrar en **nombre de producto**.  
  
6.  Si lo desea, puede escribir un nombre de publicador en **nombre del publicador**.  
  
## <a name="see-also"></a>Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)