---
title: "Cómo: volver a habilitar un complemento de VSTO que se ha deshabilitado | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.Warning.DisabledAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disabled add-ins
- add-ins [Office development in Visual Studio], disabled
- add-ins [Office development in Visual Studio], enabling
ms.assetid: 69719a0a-984c-42cd-80a2-1367c866e5df
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d89215c759b4fabc48f697100f2935d0fa33e5ab
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-re-enable-a-vsto-add-in-that-has-been-disabled"></a>Cómo: Volver a habilitar un complemento de VSTO que se ha deshabilitado
  Las aplicaciones de Microsoft Office pueden deshabilitar los complementos de VSTO que se comporten de forma inesperada. Si una aplicación no carga el complemento de VSTO cuando intenta depurarlo, la aplicación podría haber deshabilitado total o parcialmente el complemento de VSTO.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="hard-disabled-vsto-add-ins"></a>Complementos de VSTO deshabilitados totalmente  
 La deshabilitación total puede producirse cuando un complemento de VSTO hace que la aplicación se cierre inesperadamente. También puede ocurrir en el equipo de desarrollo si detiene el depurador mientras se está ejecutando el controlador de eventos <xref:Microsoft.Office.Tools.AddIn.Startup> en el complemento de VSTO.  
  
#### <a name="to-re-enable-a-vsto-add-in"></a>Para volver a habilitar un complemento de VSTO  
  
1.  En la aplicación, haga clic en la pestaña **Archivo** .  
  
2.  Haga clic en el *ApplicationName* **opciones** botón.  
  
3.  En el panel de categorías, haga clic en **Complementos**.  
  
4.  En el panel de detalles, compruebe que el complemento de VSTO aparece en la lista **Complementos de aplicación deshabilitados** .  
  
     La columna **Nombre** especifica el nombre del ensamblado y la columna **Ubicación** especifica la ruta de acceso completa del manifiesto de aplicación.  
  
5.  En el cuadro **Administrar** , haga clic en **Elementos deshabilitados**y, a continuación, haga clic en **Ir**.  
  
6.  Seleccione el complemento de VSTO y haga clic en **Habilitar**.  
  
7.  Haga clic en **Cerrar**.  
  
## <a name="soft-disabled-vsto-add-ins"></a>Complementos de VSTO deshabilitados parcialmente  
 La deshabilitación parcial puede producirse cuando un complemento de VSTO genera un error que no hace que la aplicación se cierre inesperadamente. Por ejemplo, una aplicación podría deshabilitar parcialmente un complemento de VSTO si produce una excepción no controlada mientras se ejecuta el controlador de eventos <xref:Microsoft.Office.Tools.AddIn.Startup> .  
  
> [!NOTE]  
>  Al volver a habilitar un complemento de VSTO deshabilitado parcialmente, la aplicación intenta cargar el complemento de VSTO de inmediato. Si no se corrige el problema que hizo inicialmente que la aplicación deshabilitara parcialmente el complemento de VSTO, la aplicación volverá a deshabilitar parcialmente el complemento de VSTO.  
  
#### <a name="to-re-enable-an-vsto-add-in"></a>Para volver a habilitar un complemento de VSTO  
  
1.  En la aplicación, haga clic en la pestaña **Archivo** .  
  
2.  Haga clic en el *ApplicationName* **opciones** botón.  
  
3.  En el panel de categorías, haga clic en **Complementos**.  
  
4.  En el panel de detalles, compruebe que el complemento de VSTO aparece en la lista **Complementos de aplicación inactivos** .  
  
     La columna **Nombre** especifica el nombre del ensamblado y la columna **Ubicación** especifica la ruta de acceso completa del manifiesto de aplicación.  
  
5.  En el cuadro **Administrar** , haga clic en **Complementos COM**y, a continuación, haga clic en **Ir**.  
  
6.  En el cuadro de diálogo **Complementos COM** , seleccione la casilla situada al lado del complemento de VSTO deshabilitado.  
  
7.  Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Compilar soluciones de Office](../vsto/building-office-solutions.md)   
 [Depurar proyectos de Office](../vsto/debugging-office-projects.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)  
  
  