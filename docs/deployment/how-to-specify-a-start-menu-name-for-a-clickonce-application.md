---
title: Especificar el nombre del menú Inicio para una aplicación ClickOnce
description: Obtenga información sobre cómo cambiar el nombre para mostrar de la aplicación ClickOnce estableciendo el nombre del producto en el cuadro de diálogo Opciones de publicación.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12a6ebce0ff3bb7c3040765c1a82f876d0055c4d
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349677"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Cómo: Especificar un nombre en el menú Inicio para una aplicación ClickOnce
Cuando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se instala una aplicación para su uso en línea y sin conexión, se agrega una entrada al menú **Inicio** y a la lista **Agregar o quitar programas** . De forma predeterminada, el nombre para mostrar es el mismo que el nombre del ensamblado de la aplicación, pero puede cambiar el nombre para mostrar estableciendo el **nombre del producto** en el cuadro de diálogo **Opciones de publicación** .

 El **nombre del producto** se mostrará en la página *publish.htm* ; en el caso de una aplicación sin conexión instalada, será el nombre de la entrada en el menú **Inicio** y también será el nombre que se muestra en **Agregar o quitar programas**.

 El **nombre del publicador** aparecerá en la página *publish.htm* encima del **nombre del producto** y, en el caso de una aplicación sin conexión instalada, también será el nombre de la carpeta que contiene el icono de la aplicación en el menú **Inicio** .

 El acceso directo del menú Inicio o la referencia de la aplicación se crean en *%AppData%\Microsoft\Windows\Start inicio\programas \\<nombre \> del publicador*. El acceso directo o la referencia de aplicación tienen el mismo nombre que el nombre del producto.

 Puede establecer las propiedades **nombre del producto** y **nombre del publicador** en el cuadro de diálogo **Opciones de publicación** , disponible en la página **publicar** del **Diseñador de proyectos**.

### <a name="to-specify-a-start-menu-name"></a>Para especificar un nombre de menú Inicio

1. Seleccione un proyecto en el **Explorador de soluciones** y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Publicar**.

3. Haga clic en el botón **Opciones** para abrir el cuadro de diálogo **Opciones de publicación** .

4. Haga clic en **Descripción**.

5. En el cuadro de diálogo **Opciones de publicación** , escriba el nombre que se mostrará en **nombre del producto**.

6. Opcionalmente, puede escribir un nombre de publicador en **el nombre del publicador**.

## <a name="see-also"></a>Vea también
- [Publicación de aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)