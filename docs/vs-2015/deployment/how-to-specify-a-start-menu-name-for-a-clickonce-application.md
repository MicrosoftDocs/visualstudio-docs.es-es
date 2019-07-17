---
title: Procedimiento Especifique un nombre de menú de inicio para una aplicación ClickOnce | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 30bb4050399bf7a6d9120f7e5454b26ce505af35
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149762"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Procedimiento Especificar un nombre de menú Inicio para una aplicación ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] se instala la aplicación para su uso en línea y sin conexión, se agrega una entrada para el **iniciar** menú y el **agregar o quitar programas** lista. De forma predeterminada, el nombre para mostrar es el mismo que el nombre del ensamblado de la aplicación, pero puede cambiar el nombre para mostrar estableciendo **nombre de producto** en el **opciones de publicación** cuadro de diálogo.  
  
 **Nombre de producto** se mostrará en la página publish.htm; para una aplicación instalada sin conexión, será el nombre de la entrada en el **iniciar** menú y, también será el nombre que se muestra en **agregar o quitar Programas**.  
  
 **Nombre del publicador** aparecerá en la página publish.htm anterior **nombre de producto**, y para una aplicación instalada sin conexión, también será el nombre de la carpeta que contiene el icono de la aplicación en el **iniciar**  menú.  
  
 Puede establecer el **nombre de producto** y **nombre del publicador** propiedades en el **opciones de publicación** cuadro de diálogo, disponible en el **publicar** página de la **Diseñador de proyectos**.  
  
### <a name="to-specify-a-start-menu-name"></a>Para especificar un nombre de menú Inicio  
  
1. Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2. Haga clic en la pestaña **Publicar**.  
  
3. Haga clic en el **opciones** botón para abrir el **opciones de publicación** cuadro de diálogo.  
  
4. Haga clic en **descripción**.  
  
5. En el **opciones de publicación** diálogo cuadro, escriba el nombre para mostrar en **nombre de producto**.  
  
6. Si lo desea, puede escribir un nombre de publicador en **nombre del publicador**.  
  
## <a name="see-also"></a>Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicación de una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
