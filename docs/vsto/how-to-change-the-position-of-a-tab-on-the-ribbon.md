---
title: "Cómo: cambiar la posición de una pestaña en la cinta de opciones | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: Ribbon [Office development in Visual Studio], tabs
ms.assetid: 3f0906e3-9708-4136-ac49-986bc4c92ea4
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 196b16ba28ee5fa590c54dee89dcd65978f2ecd2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>Cómo: Cambiar la posición de una pestaña en la cinta de opciones
  Puede cambiar el orden de las fichas personalizadas en una cinta de opciones mediante la **pestaña Editor de la colección**. Puede colocar pestañas personalizadas antes o después de una pestaña integrada en la cinta de opciones. Una pestaña integrada es una pestaña que ya está en la cinta de opciones de una aplicación de Microsoft Office. Por ejemplo, el **datos** ficha es una pestaña integrada en Excel.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>Para cambiar el orden de las fichas de la cinta de opciones  
  
1.  Seleccione el archivo de código de la cinta de opciones (archivo .vb o. cs) en **el Explorador de soluciones**.  
  
2.  En el **vista** menú, haga clic en **diseñador**.  
  
3.  Haga clic en el Diseñador de la cinta de opciones y, a continuación, haga clic en **propiedades**.  
  
4.  En el **propiedades** ventana, seleccione la **pestañas** propiedad y, a continuación, haga clic en el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Elipse del Diseñador de")).  
  
     El **Editor de la colección de ficha** aparece.  
  
5.  En el **Editor de la colección de ficha**, en la **miembros** , seleccione la ficha que desee mover y haga clic en arriba o abajo las flechas para cambiar el orden de tabulación.  
  
### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>Para colocar una ficha antes o después de una pestaña integrada en la cinta de opciones  
  
1.  En el Diseñador de la cinta de opciones, seleccione una ficha personalizada.  
  
2.  En el **propiedades** ventana, expanda la **ControlId** propiedad y, a continuación, asegúrese de que el valor de la **ControlIdType** propiedad está establecida en **personalizado**.  
  
3.  En el **propiedades** ventana, expanda la **posición** propiedad.  
  
4.  Establecer el **PositionType** propiedad en el valor adecuado:  
  
    -   **BeforeOfficeId** coloca el grupo antes de una pestaña integrada especificado.  
  
    -   **AfterOfficeId** coloca el grupo después de una pestaña integrada especificada.  
  
5.  Establecer el **OfficeId** propiedad para el Id. de control de una pestaña integrada.  
  
     Para obtener una lista de identificadores de control, vea [archivos de Ayuda de Office 2010: identificadores de Control en la interfaz de usuario de Office Fluent](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## <a name="see-also"></a>Vea también  
 [Información general de la cinta de opciones](../vsto/ribbon-overview.md)   
 [Diseñador de la cinta](../vsto/ribbon-designer.md)   
 [XML de la cinta de opciones](../vsto/ribbon-xml.md)   
 [Tutorial: Crear una pestaña personalizada usando el Diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Tutorial: Creación de una pestaña personalizada mediante XML de la cinta](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  